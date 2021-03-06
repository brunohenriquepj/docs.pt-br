---
title: '&lt;proxy&gt; elemento (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b5ae716994f9b8222a633699367c94480179c97b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744441"
---
# <a name="ltproxygt-element-network-settings"></a>&lt;proxy&gt; elemento (configurações de rede)
Define um servidor proxy.  
  
 \<configuration>  
\<system.net>  
\<defaultProxy >  
\<proxy >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|**Atributo**|**Descrição**|  
|-------------------|---------------------|  
|`autoDetect`|Especifica se o proxy é detectado automaticamente. O valor padrão é `unspecified`.|  
|`bypassonlocal`|Especifica se o proxy é ignorado para os recursos locais. Recursos locais incluem o servidor local (http://localhost, http://loopback, ou http://127.0.0.1) e um URI sem um período (http://webserver). O valor padrão é `unspecified`.|  
|`proxyaddress`|Especifica o URI para usar proxy.|  
|`scriptLocation`|Especifica o local do script de configuração.|  
|`usesystemdefault`|Especifica se deve usar configurações de proxy do Internet Explorer. Se definido como `true`, os atributos subsequentes substituirão as configurações de proxy do Internet Explorer. O valor padrão é `unspecified`.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Configura o servidor de proxy do protocolo HTTP (Hypertext Transfer).|  
  
## <a name="text-value"></a>Valor de texto  
  
## <a name="remarks"></a>Comentários  
 O `proxy` elemento define um servidor proxy para um aplicativo. Se esse elemento está ausente do arquivo de configuração, o .NET Framework usará as configurações de proxy no Internet Explorer.  
  
 O valor para o `proxyaddress` atributo deve ser um URI bem formado Uniform Resource indicador ().  
  
 O `scriptLocation` atributo refere-se a detecção automática de scripts de configuração de proxy. O <xref:System.Net.WebProxy> classe tentará localizar um script de configuração (geralmente nomeado WPAD) quando o **usar script de configuração automática** está selecionada no Internet Explorer.  
  
 Use o `usesystemdefault` atributo para aplicativos do .NET Framework versão 1.1 que está migrando para a versão 2.0.  
  
 Uma exceção será lançada se o `proxyaddress` atributo especifica um proxy padrão inválido. O <xref:System.Exception.InnerException%2A> propriedade sobre a exceção deve ter mais informações sobre a causa do erro.  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa os padrões do proxy do Internet Explorer, especifica o endereço de proxy e ignora o proxy para acesso local.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
