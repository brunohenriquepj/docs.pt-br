---
title: Configuração de proxy
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 41e1dcee90531de605b6bddc1eedc1c44235d8eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397527"
---
# <a name="proxy-configuration"></a>Configuração de proxy
Um servidor proxy manipula as solicitações de clientes para recursos. Um proxy pode retornar um recurso solicitado do seu cache ou encaminhar a solicitação para o servidor na qual o recurso reside. Proxies podem melhorar o desempenho da rede, reduzindo o número de solicitações enviadas a servidores remotos. Proxies também podem ser usados para restringir o acesso aos recursos.  
  
## <a name="adaptive-proxies"></a>Proxies adaptáveis  
 No .NET Framework, os proxies existem em duas variedades: adaptáveis e estáticos. Proxies adaptáveis ajustam suas configurações quando as configurações de rede são alteradas. Por exemplo, se um usuário de laptop inicia uma conexão de rede dial-up, um proxy adaptável reconheceria essa alteração, descobrir e executaria seu novo script de configuração e ajustaria suas configurações adequadamente.  
  
 Proxies adaptáveis são configurados por um script de configuração (consulte [Detecção automática de proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)). O script gera um conjunto de protocolos de aplicativo e um proxy para cada protocolo.  
  
 Várias opções de controlam a maneira como o script de configuração é executado. Você pode especificar o seguinte:  
  
-   A frequência com que o script de configuração é baixado e executado.  
  
-   Tempo de espera para o download do script.  
  
-   Quais credenciais seu sistema deve usar para acessar o proxy.  
  
-   Quais credenciais seu sistema deve usar para baixar o script de configuração.  
  
 Alterações no ambiente de rede podem exigir que o sistema use um novo conjunto de proxies. Se uma conexão de rede ficar inoperante ou uma nova conexão de rede for inicializada, o sistema deve descobrir a origem correta do script de configuração no novo ambiente e executar o novo script.  
  
 A tabela a seguir mostra as opções de configuração para um proxy adaptável.  
  
|Definição do arquivo de configuração, propriedade ou atributo|Descrição|  
|--------------------------------------------------------|-----------------|  
|`scriptDownloadInterval`|Tempo decorrido em segundos entre downloads de script.|  
|`scriptDownloadTimeout`|Tempo de espera (em segundos) para baixar o script.|  
|`useDefaultCredentials` ou <xref:System.Net.WebProxy.UseDefaultCredentials>|Controla se o sistema usa as credenciais de rede padrão para acessar um proxy.|  
|`useDefaultCredentialForScriptDownload`|Controla se o sistema usa as credenciais de rede padrão para baixar o script de configuração.|  
|`usesystemdefaults`|Controla se as configurações de proxy estático (endereço de proxy, lista de ignoráveis e ignorar no local) devem ser lido das configurações de proxy do Internet Explorer para o usuário. Se esse valor for definido como "true", as configurações de proxy estático do Internet Explorer serão usadas.<br /><br /> Se esse valor for "false" ou se não estiver definido, as configurações de proxy estático podem ser especificadas na configuração e substituirão as configurações de proxy do Internet Explorer. Esse valor também deve ser definido como "false" ou não estar configurado para habilitar proxies adaptáveis.|  
  
 O exemplo a seguir mostra uma configuração de proxy adaptável típica.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy  scriptDownloadInterval="600"  
              scriptDownloadTimeout="30"  
              useDefaultCredentials="true"  
              usesystemdefaults="true"  
      />  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Proxies estáticos  
 Proxies estáticos geralmente são configurados explicitamente por um aplicativo ou quando um arquivo de configuração é invocado por um aplicativo ou pelo sistema. Proxies estáticos são úteis em redes em que a topologia é alterada com frequência, como um computador desktop conectado a uma rede corporativa.  
  
 Várias opções de controlam como um proxy estático funciona. Você pode especificar o seguinte:  
  
-   O endereço do proxy.  
  
-   Se o proxy deve ou não ser ignorado para endereços locais.  
  
-   Se o proxy deve ou não ser ignorado para um conjunto de endereços.  
  
 A tabela a seguir mostra as opções de configuração para um proxy estático.  
  
|Definição do arquivo de configuração, propriedade ou atributo|Descrição|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` ou <xref:System.Net.WebProxy.Address>|O endereço do proxy a ser usado.|  
|`bypassonlocal` ou <xref:System.Net.WebProxy.BypassProxyOnLocal>|Controla se o proxy é ignorado para endereços locais.|  
|`bypasslist` ou <xref:System.Net.WebProxy.BypassArrayList>|Descreve, com expressões regulares, um conjunto de endereços que ignora o proxy.|  
|`usesystemdefaults`|Controla se as configurações de proxy estático (endereço de proxy, lista de ignoráveis e ignorar no local) devem ser lido das configurações de proxy do Internet Explorer para o usuário. Se esse valor for definido como "true", as configurações de proxy estático do Internet Explorer serão usadas. No .NET Framework 2.0, quando esse valor é definido como "true", as configurações de proxy do Internet Explorer não são substituídas por outras configurações de proxy no arquivo de configurações. No .NET Framework 1.1, as configurações de proxy do Internet Explorer podem ser substituídas por outras configurações de proxy no arquivo de configuração.<br /><br /> Se esse valor for "false" ou se não estiver definido, as configurações de proxy estático podem ser especificadas na configuração e substituirão as configurações de proxy do Internet Explorer. Esse valor também deve ser definido como "false" ou não estar configurado para habilitar proxies adaptáveis.|  
  
 O exemplo a seguir mostra uma configuração de proxy estático típica.  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="true"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [Detecção automática de proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)
