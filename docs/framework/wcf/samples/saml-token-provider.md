---
title: Fornecedor de token SAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fc6eaa916507c7e1c530d4ee757097bf0bffcd34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="saml-token-provider"></a><span data-ttu-id="ac1b3-102">Fornecedor de token SAML</span><span class="sxs-lookup"><span data-stu-id="ac1b3-102">SAML Token Provider</span></span>
<span data-ttu-id="ac1b3-103">Este exemplo demonstra como implementar um provedor de token SAML de cliente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-103">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="ac1b3-104">Um provedor de token em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é usado para fornecer credenciais para a infraestrutura de segurança.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-104">A token provider in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="ac1b3-105">O provedor de token em geral examina o destino e problemas apropriada credenciais para que a infraestrutura de segurança possa proteger a mensagem.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ac1b3-106">é fornecido com o provedor de Token do Gerenciador de credenciais padrão.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-106"> ships with the default Credential Manager Token Provider.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ac1b3-107">também é fornecida com um [!INCLUDE[infocard](../../../../includes/infocard-md.md)] provedor de token.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-107"> also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="ac1b3-108">Provedores de token personalizados são úteis nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="ac1b3-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="ac1b3-109">Se você tiver um repositório de credenciais que esses provedores de token não podem operar com.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-109">If you have a credential store that these token providers cannot operate with.</span></span>  
  
-   <span data-ttu-id="ac1b3-110">Se desejar fornecer seu próprio mecanismo personalizado para transformar as credenciais do ponto quando o usuário fornece os detalhes para quando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estrutura do cliente usa as credenciais.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework uses the credentials.</span></span>  
  
-   <span data-ttu-id="ac1b3-111">Se você estiver criando um token personalizado.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="ac1b3-112">Este exemplo mostra como criar um provedor de token personalizado que permite que um token SAML obtido fora do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estrutura do cliente a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-112">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework to be used.</span></span>  
  
 <span data-ttu-id="ac1b3-113">Para resumir, este exemplo demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ac1b3-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="ac1b3-114">Como um cliente pode ser configurado com um provedor do token.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-114">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="ac1b3-115">Como um token SAML pode ser passado para as credenciais de cliente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-115">How a SAML token can be passed to the custom client credentials.</span></span>  
  
-   <span data-ttu-id="ac1b3-116">Como o token SAML é fornecido para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estrutura do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-116">How the SAML token is provided to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework.</span></span>  
  
-   <span data-ttu-id="ac1b3-117">Como o servidor é autenticado pelo cliente usando o certificado do servidor x. 509.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="ac1b3-118">O serviço expõe dois pontos de extremidade de comunicação com o serviço, definido usando o arquivo de configuração App. config. Cada ponto de extremidade consiste em um endereço, uma ligação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-118">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="ac1b3-119">A associação está configurada com um padrão `wsFederationHttpBinding`, que usa segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-119">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="ac1b3-120">Um ponto de extremidade espera que o cliente para autenticar com um token SAML que usa uma chave de prova simétrica enquanto o outro espera que o cliente para autenticar com um token SAML que usa uma chave assimétrica de prova.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-120">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="ac1b3-121">O serviço também configura o certificado de serviço usando `serviceCredentials` comportamento.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-121">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="ac1b3-122">O `serviceCredentials` comportamento permite que você configure um certificado de serviço.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-122">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="ac1b3-123">Um certificado de serviço é usado por um cliente para autenticar o serviço e fornecer proteção de mensagem.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-123">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="ac1b3-124">A configuração a seguir faz referência ao certificado de "localhost" instalado durante a configuração de exemplo, conforme descrito nas instruções de instalação no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-124">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="ac1b3-125">O `serviceCredentials` comportamento também permite que você configure os certificados que são confiáveis para autenticar os tokens SAML.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-125">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="ac1b3-126">A configuração a seguir faz referência ao certificado de 'Alice' instalado durante a amostragem.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-126">The following configuration references the 'Alice' certificate installed during the sample.</span></span>  
  
```xml  
<system.serviceModel>  
 <services>  
  <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
   <host>  
    <baseAddresses>  
     <!-- configure base address provided by host -->  
     <add    
  baseAddress="http://localhost:8000/servicemodelsamples/service/" />  
    </baseAddresses>  
   </host>  
   <!-- use base address provided by host -->  
   <!-- Endpoint that expect SAML tokens with Symmetric proof keys -->  
   <endpoint address="calc/symm"  
             binding="wsFederationHttpBinding"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   <!-- Endpoint that expect SAML tokens with Asymmetric proof keys -->  
   <endpoint address="calc/asymm"  
             binding="wsFederationHttpBinding"  
             bindingConfiguration="Binding2"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </service>  
 </services>  
  
 <bindings>  
  <wsFederationHttpBinding>  
   <!-- Binding that expect SAML tokens with Symmetric proof keys -->  
   <binding name="Binding1">  
    <security mode="Message">  
     <message negotiateServiceCredential ="false"   
              issuedKeyType="SymmetricKey"   
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />  
    </security>  
   </binding>  
   <!-- Binding that expect SAML tokens with Asymmetric proof keys -->  
   <binding name="Binding2">  
    <security mode="Message">  
     <message negotiateServiceCredential ="false"  
              issuedKeyType="AsymmetricKey"   
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />  
    </security>  
   </binding>          
  </wsFederationHttpBinding>  
 </bindings>  
  
 <behaviors>  
  <serviceBehaviors>  
   <behavior name="CalculatorServiceBehavior">  
    <!--   
    The serviceCredentials behavior allows one to define a service certificate.  
    A service certificate is used by a client to authenticate the service and provide message protection.  
    This configuration references the "localhost" certificate installed during the setup instructions.  
    -->  
    <serviceCredentials>  
     <!-- Set allowUntrustedRsaIssuers to true to allow self-signed, asymmetric key based SAML tokens -->  
     <issuedTokenAuthentication allowUntrustedRsaIssuers ="true" >  
      <!-- Add Alice to the list of certs trusted to issue SAML tokens -->  
      <knownCertificates>  
       <add storeLocation="LocalMachine"   
            storeName="TrustedPeople"   
            x509FindType="FindBySubjectName"   
            findValue="Alice"/>  
      </knownCertificates>  
     </issuedTokenAuthentication>  
     <serviceCertificate storeLocation="LocalMachine"  
                         storeName="My"  
                         x509FindType="FindBySubjectName"  
                         findValue="localhost"  />  
    </serviceCredentials>  
   </behavior>  
  </serviceBehaviors>  
 </behaviors>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="ac1b3-127">As etapas a seguir mostram como desenvolver um provedor do token SAML e integrá-lo ao [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: estrutura de segurança:</span><span class="sxs-lookup"><span data-stu-id="ac1b3-127">The following steps show how to develop a custom SAML token provider and integrate it with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: security framework:</span></span>  
  
1.  <span data-ttu-id="ac1b3-128">Grave um provedor do token SAML.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-128">Write a custom SAML token provider.</span></span>  
  
     <span data-ttu-id="ac1b3-129">O exemplo implementa um provedor de token de SAML personalizado que retorna um token de segurança com base em uma asserção SAML que é fornecida no tempo de construção.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-129">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>  
  
     <span data-ttu-id="ac1b3-130">Para executar essa tarefa, o provedor do token é derivado do <xref:System.IdentityModel.Selectors.SecurityTokenProvider> classe e substituições de <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> método.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-130">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="ac1b3-131">Esse método cria e retorna um novo `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-131">This method creates and returns a new `SecurityToken`.</span></span>  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
     // Create a SamlSecurityToken from the provided assertion  
     SamlSecurityToken samlToken = new SamlSecurityToken(assertion);  
  
     // Create a SecurityTokenSerializer that will be used to   
     // serialize the SamlSecurityToken  
     WSSecurityTokenSerializer ser = new WSSecurityTokenSerializer();  
     // Create a memory stream to write the serialized token into  
     // Use an initial size of 64Kb  
     MemoryStream s = new MemoryStream(UInt16.MaxValue);  
  
     // Create an XmlWriter over the stream  
     XmlWriter xw = XmlWriter.Create(s);  
  
     // Write the SamlSecurityToken into the stream  
     ser.WriteToken(xw, samlToken);  
  
     // Seek back to the beginning of the stream  
     s.Seek(0, SeekOrigin.Begin);  
  
     // Load the serialized token into a DOM  
     XmlDocument dom = new XmlDocument();  
     dom.Load(s);  
  
     // Create a KeyIdentifierClause for the SamlSecurityToken  
     SamlAssertionKeyIdentifierClause samlKeyIdentifierClause = samlToken.CreateKeyIdentifierClause<SamlAssertionKeyIdentifierClause>();  
  
    // Return a GenericXmlToken from the XML for the   
    // SamlSecurityToken, the proof token, the valid from and valid  
    // until times from the assertion and the key identifier clause  
    // created above  
    return new GenericXmlSecurityToken(dom.DocumentElement, proofToken, assertion.Conditions.NotBefore, assertion.Conditions.NotOnOrAfter, samlKeyIdentifierClause, samlKeyIdentifierClause, null);  
    }  
    ```  
  
2.  <span data-ttu-id="ac1b3-132">Grave o Gerenciador de token de segurança personalizada.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-132">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="ac1b3-133">O <xref:System.IdentityModel.Selectors.SecurityTokenManager> classe é usada para criar <xref:System.IdentityModel.Selectors.SecurityTokenProvider> para determinado <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> que é passado para ele no `CreateSecurityTokenProvider` método.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-133">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="ac1b3-134">Um Gerenciador de token de segurança também é usado para criar o serializador de token e autenticadores de token, mas aqueles não são cobertas por este exemplo.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-134">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="ac1b3-135">Neste exemplo de segurança personalizada herda do Gerenciador de token o <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> classe e substituições de `CreateSecurityTokenProvider` método para retornar o provedor do token SAML quando os requisitos de token passados indicam que o token SAML é solicitado.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-135">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="ac1b3-136">Se a classe de credenciais de cliente (consulte a etapa 3) não tiver especificado uma asserção, o Gerenciador de token de segurança cria uma instância apropriada.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-136">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>  
  
    ```  
    public class SamlSecurityTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
     SamlClientCredentials samlClientCredentials;  
  
     public SamlSecurityTokenManager ( SamlClientCredentials samlClientCredentials)  
      : base(samlClientCredentials)  
     {  
      // Store the creating client credentials  
      this.samlClientCredentials = samlClientCredentials;  
     }  
  
     public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
     {  
      // If token requirement matches SAML token return the   
      // custom SAML token provider  
      if (tokenRequirement.TokenType == SecurityTokenTypes.Saml ||  
          tokenRequirement.TokenType == "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1")  
      {  
       // Retrieve the SAML assertion and proof token from the   
       // client credentials  
       SamlAssertion assertion = this.samlClientCredentials.Assertion;  
       SecurityToken prooftoken = this.samlClientCredentials.ProofToken;  
  
       // If either the assertion of proof token is null...  
       if (assertion == null || prooftoken == null)  
       {  
        // ...get the SecurityBindingElement and then the   
        // specified algorithm suite  
        SecurityBindingElement sbe = null;  
        SecurityAlgorithmSuite sas = null;  
  
        if ( tokenRequirement.TryGetProperty<SecurityBindingElement> ( "http://schemas.microsoft.com/ws/2006/05/servicemodel/securitytokenrequirement/SecurityBindingElement", out sbe))  
        {  
         sas = sbe.DefaultAlgorithmSuite;  
        }  
  
        // If the token requirement is for a SymmetricKey based token..  
        if (tokenRequirement.KeyType == SecurityKeyType.SymmetricKey)  
        {  
         // Create a symmetric proof token  
         prooftoken = SamlUtilities.CreateSymmetricProofToken ( tokenRequirement.KeySize );  
         // and a corresponding assertion based on the claims specified in the client credentials  
         assertion = SamlUtilities.CreateSymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, new X509SecurityToken ( samlClientCredentials.ClientCertificate.Certificate ), new X509SecurityToken ( samlClientCredentials.ServiceCertificate.DefaultCertificate ), (BinarySecretSecurityToken)prooftoken, sas);  
        }  
        // otherwise...  
        else  
        {  
         // Create an asymmetric proof token  
         prooftoken = SamlUtilities.CreateAsymmetricProofToken();  
         // and a corresponding assertion based on the claims   
         // specified in the client credentials  
         assertion = SamlUtilities.CreateAsymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, prooftoken, sas );  
        }  
       }  
  
       // Create a SamlSecurityTokenProvider based on the assertion and proof token  
       return new SamlSecurityTokenProvider(assertion, prooftoken);  
      }  
      // otherwise use base implementation  
      else  
      {  
       return base.CreateSecurityTokenProvider(tokenRequirement);  
      }  
    }  
    ```  
  
3.  <span data-ttu-id="ac1b3-137">Grave uma credencial de cliente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-137">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="ac1b3-138">Classe de credenciais de cliente é usado para representar as credenciais que são configuradas para o proxy de cliente e cria o Gerenciador de token que é usado para obter o serializador de token, provedores de token e autenticadores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-138">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>  
  
    ```  
    public class SamlClientCredentials : ClientCredentials  
    {  
     ClaimSet claims;  
     SamlAssertion assertion;  
     SecurityToken proofToken;  
  
     public SamlClientCredentials() : base()  
     {  
      // Set SupportInteractive to false to suppress Cardspace UI  
      base.SupportInteractive = false;  
     }  
  
     protected SamlClientCredentials(SamlClientCredentials other) : base ( other )  
     {  
      // Just do reference copy given sample nature  
      this.assertion = other.assertion;  
      this.claims = other.claims;  
      this.proofToken = other.proofToken;  
     }  
  
     public SamlAssertion Assertion { get { return assertion; } set { assertion = value; } }  
  
     public SecurityToken ProofToken { get { return proofToken; } set { proofToken = value; } }  
     public ClaimSet Claims { get { return claims; } set { claims = value; } }  
  
     protected override ClientCredentials CloneCore()  
     {  
      return new SamlClientCredentials(this);  
     }  
  
     public override SecurityTokenManager CreateSecurityTokenManager()  
     {  
      // return custom security token manager  
      return new SamlSecurityTokenManager(this);  
     }  
    }  
    ```  
  
4.  <span data-ttu-id="ac1b3-139">Configure o cliente para usar a credencial de cliente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-139">Configure the client to use the custom client credential.</span></span>  
  
     <span data-ttu-id="ac1b3-140">O exemplo exclui a classe de credencial de cliente padrão e fornece a nova classe de credencial de cliente para que o cliente pode usar a credencial de cliente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-140">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>  
  
    ```  
    // Create new credentials class  
    SamlClientCredentials samlCC = new SamlClientCredentials();  
  
    // Set the client certificate. This is the cert that will be used to sign the SAML token in the symmetric proof key case  
    samlCC.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "Alice");  
  
    // Set the service certificate. This is the cert that will be used to encrypt the proof key in the symmetric proof key case  
    samlCC.ServiceCertificate.SetDefaultCertificate(StoreLocation.CurrentUser, StoreName.TrustedPeople, X509FindType.FindBySubjectName, "localhost");  
  
    // Create some claims to put in the SAML assertion  
    IList<Claim> claims = new List<Claim>();  
    claims.Add(Claim.CreateNameClaim(samlCC.ClientCertificate.Certificate.Subject));  
    ClaimSet claimset = new DefaultClaimSet(claims);  
    samlCC.Claims = claimset;  
  
    // set new credentials  
    client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));  
    client.ChannelFactory.Endpoint.Behaviors.Add(samlCC);  
    ```  
  
 <span data-ttu-id="ac1b3-141">Sobre o serviço, as declarações associadas ao chamador são exibidas.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-141">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="ac1b3-142">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-142">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ac1b3-143">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-143">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="ac1b3-144">Arquivo de lote</span><span class="sxs-lookup"><span data-stu-id="ac1b3-144">Setup Batch File</span></span>  
 <span data-ttu-id="ac1b3-145">Arquivo em lotes bat incluído com este exemplo permite que você configure o servidor com o certificado apropriado para executar um aplicativo auto-hospedado que exige a segurança baseada em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-145">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="ac1b3-146">Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso não hospedado.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-146">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="ac1b3-147">O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-147">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="ac1b3-148">Criando o certificado do servidor:</span><span class="sxs-lookup"><span data-stu-id="ac1b3-148">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="ac1b3-149">As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-149">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="ac1b3-150">O `%SERVER_NAME%` variável Especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-150">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="ac1b3-151">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-151">Change this variable to specify your own server name.</span></span> <span data-ttu-id="ac1b3-152">O valor padrão, esse arquivo em lotes é localhost.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-152">The default value in this batch file is localhost.</span></span>  
  
     <span data-ttu-id="ac1b3-153">O certificado é armazenado no repositório My (pessoal) em um local de repositório LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-153">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="ac1b3-154">Instalando o certificado do servidor no repositório de certificados confiáveis do cliente:</span><span class="sxs-lookup"><span data-stu-id="ac1b3-154">Installing the server certificate into the client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="ac1b3-155">Armazenam as linhas a seguir na cópia de arquivo de lote o certificado do servidor bat para as pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-155">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="ac1b3-156">Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-156">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ac1b3-157">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-157">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="ac1b3-158">Criando o certificado do emissor.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-158">Creating the issuer certificate.</span></span>  
  
     <span data-ttu-id="ac1b3-159">As seguintes linhas do arquivo em lotes bat criam o certificado do emissor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-159">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="ac1b3-160">O `%USER_NAME%` variável Especifica o nome do emissor.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-160">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="ac1b3-161">Altere essa variável para especificar seu próprio nome de emissor.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-161">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="ac1b3-162">O valor padrão, esse arquivo em lotes é Alice.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-162">The default value in this batch file is Alice.</span></span>  
  
     <span data-ttu-id="ac1b3-163">O certificado é armazenado no meu repositório no local de armazenamento CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-163">The certificate is stored in My store under the CurrentUser store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="ac1b3-164">Instalando o certificado do emissor no repositório de certificados confiáveis do servidor.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-164">Installing the issuer certificate into the server's trusted certificate store.</span></span>  
  
     <span data-ttu-id="ac1b3-165">Armazenam as linhas a seguir na cópia de arquivo de lote o certificado do servidor bat para as pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-165">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="ac1b3-166">Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-166">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ac1b3-167">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preenchimento do repositório de certificados do servidor com o certificado do emissor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-167">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="ac1b3-168">Para configurar e criar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ac1b3-168">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="ac1b3-169">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ac1b3-169">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ac1b3-170">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ac1b3-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac1b3-171">Se você usar o Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-171">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="ac1b3-172">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="ac1b3-172">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="ac1b3-173">Execute bat da pasta de instalação de exemplo dentro de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prompt de comando executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-173">Run Setup.bat from the sample installation folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt run with administrator privileges.</span></span> <span data-ttu-id="ac1b3-174">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-174">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac1b3-175">O arquivo em lotes bat é projetado para ser executado de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-175">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="ac1b3-176">Definir a variável de ambiente PATH dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém os executáveis exigido pelo script bat.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-176">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="ac1b3-177">Inicie Service.exe de service\bin.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-177">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="ac1b3-178">Inicie Client.exe de \Client\Bin.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="ac1b3-179">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-179">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="ac1b3-180">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="ac1b3-180">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="ac1b3-181">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="ac1b3-181">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="ac1b3-182">Crie um diretório no computador de serviço para os binários de serviço.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-182">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="ac1b3-183">Copie os arquivos de programa do serviço para o diretório de serviço no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-183">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="ac1b3-184">Também copie os arquivos. bat e Cleanup.bat para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-184">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="ac1b3-185">Você deve ter um certificado de servidor com o nome da entidade que contém o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-185">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="ac1b3-186">O arquivo Service.exe.config deve ser atualizado para refletir o novo nome de certificado.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-186">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="ac1b3-187">Você pode criar o certificado do servidor, modificando o arquivo em lotes bat.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-187">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="ac1b3-188">Observe que o arquivo bat deve ser executado em uma janela de prompt de comando do Visual Studio aberta com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-188">Note that the setup.bat file must be run in a Visual Studio command prompt window opened with administrator privileges.</span></span> <span data-ttu-id="ac1b3-189">Você deve definir o `%SERVER_NAME%` variável para o nome de host totalmente qualificado do computador que é usado para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-189">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4.  <span data-ttu-id="ac1b3-190">Copie o certificado do servidor para o armazenamento CurrentUser TrustedPeople do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-190">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="ac1b3-191">Essa etapa não é necessária quando o certificado do servidor é emitido por um emissor confiável do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-191">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="ac1b3-192">No arquivo Service.exe.config no computador de serviço, altere o valor do endereço base para especificar um nome de computador totalmente qualificado em vez de localhost.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-192">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="ac1b3-193">No computador do serviço, execute Service.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-193">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="ac1b3-194">Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-194">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="ac1b3-195">No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-195">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="ac1b3-196">No computador cliente, inicie o `Client.exe` em uma janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-196">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="ac1b3-197">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="ac1b3-197">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ac1b3-198">A limpeza após a amostra</span><span class="sxs-lookup"><span data-stu-id="ac1b3-198">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="ac1b3-199">Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="ac1b3-199">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac1b3-200">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac1b3-200">See Also</span></span>