---
title: '&lt;certificateReference&gt;'
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e0f9a826a4c8d292346d9efee7970a82b88fb612
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756833"
---
# <a name="ltcertificatereferencegt"></a>&lt;certificateReference&gt;
Especifica configurações que são usadas para encontrar e validar um certificado x. 509 em um repositório de certificados.  
  
 \<System >  
\<federationConfiguration >  
\<serviceCertificate >  
\<certificateReference >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|storeName|O nome do repositório de certificados X.509. O padrão é "My". Opcional.|  
|storeLocation|Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o local do repositório de certificados x. 509. O valor padrão é "LocalMachine". Opcional.|  
|X509FindType|Um <xref:System.Security.Cryptography.X509Certificates.X509FindType> valor que especifica o tipo de pesquisa a ser executado. O padrão é "FindBySubjectDistinguishedName". Opcional.|  
|findValue|O valor a ser pesquisado no repositório de certificados X.509. Opcional.|  
|isChainIncluded|Especifica se a validação deve ser executada usando a cadeia de certificados. O padrão é "true"; a validação é executada usando a cadeia de certificados. Opcional.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Configura o certificado usado para criptografar e descriptografar tokens.|  
  
## <a name="remarks"></a>Comentários  
 O `<certificateReference>` elemento Especifica configurações que são usadas para localizar e validar um certificado x. 509 em um repositório de certificados. Quando ele é especificado como o elemento filho de `<serviceCertficate>` elemento, especifica as configurações de local e a verificação do certificado x. 509 que é usada para criptografar e descriptografar tokens. O `<certificateReference>` elemento é representado pela <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.
