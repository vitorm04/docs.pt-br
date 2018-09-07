---
title: Configurando HTTP e HTTPS
ms.date: 03/30/2017
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: 36dbf725dfcd6fefe6482f7de69daea9356d3d07
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087693"
---
# <a name="configuring-http-and-https"></a>Configurando HTTP e HTTPS
Os serviços e os clientes WCF podem se comunicar por HTTP e HTTPS. As configurações de HTTP/HTTPS são definidas usando o IIS (Serviços de Informações da Internet) ou uma ferramenta de linha de comando. Quando um serviço WCF é hospedado no IIS HTTP ou HTTPS, as configurações podem ser definidas no IIS (usando a ferramenta inetmgr.exe). Se um serviço WCF for auto-hospedado, as configurações de HTTP ou HTTPS serão definidas usando uma ferramenta de linha de comando.  
  
 No mínimo, você desejará configurar um registro de URL e adicionar uma exceção do Firewall para a URL que seu serviço estará usando.  
  
 A ferramenta usada para definir configurações HTTP depende do sistema operacional que o computador está executando.  
  
 Ao executar [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use a ferramenta HttpCfg.exe. O [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] instala essa ferramenta automaticamente. Ao executar [!INCLUDE[wxp](../../../../includes/wxp-md.md)], você pode baixar a ferramenta em [ferramentas de suporte do Windows XP Service Pack 2](https://go.microsoft.com/fwlink/?LinkId=88606). Para obter mais informações, consulte [visão geral de HTTPCFG&lt;2}&lt;1](https://go.microsoft.com/fwlink/?LinkId=88605).  
  
 Ao executar [!INCLUDE[wv](../../../../includes/wv-md.md)] ou Windows 7, você define essas configurações com a ferramenta Netsh.exe.  
  
## <a name="configuring-namespace-reservations"></a>Configurando reservas de namespace  
 A reserva de namespace atribui os direitos para uma parte do namespace da URL HTTP para um determinado grupo de usuários. Uma reserva dá a esses usuários o direito de criar serviços que escutam naquela parte do namespace. As reservas são prefixos de URL, o que significa que a reserva cobre todos os subcaminhos do caminho de reserva. As reservas de namespace permitem usar caracteres curinga de duas maneiras. A documentação da API de servidor HTTP descreve a [ordem de resolução de nomes entre as declarações de namespace que envolvem caracteres curinga](https://go.microsoft.com/fwlink/?LinkId=94841).  
  
 Um aplicativo em execução pode criar uma solicitação semelhante para adicionar registros de namespace. Os registros e as reservas competem por partes do namespace. Uma reserva pode ter precedência sobre um registro de acordo com a ordem de resolução determinada na [ordem de resolução de nomes entre as declarações de namespace que envolvem caracteres curinga](https://go.microsoft.com/fwlink/?LinkId=94841). Nesse caso, a reserva impede que o aplicativo em execução receba pedidos.  
  
### <a name="running-windows-xp-or-server-2003"></a>Executando o Windows XP ou Server 2003  
 Use o `httpcfg.exe set urlacl` comando para alterar as reservas de namespace. O [documentação de ferramentas de suporte do Windows](https://go.microsoft.com/fwlink/?LinkId=94840) explica a sintaxe da ferramenta Httpcfg.exe. A modificação dos direitos de reserva para uma parte do namespace exige privilégios administrativos ou de propriedade daquela parte do namespace. Inicialmente, todo o namespace HTTP pertence ao administrador local.  
  
 O seguinte mostra a sintaxe do comando Httpcfg com a opção `set urlacl`  
  
```  
httpcfg set urlacl /u {http://URL:Port/ | https://URL:Port/} /aACL  
```  
  
 O parâmetro `/u` é obrigatório ao usar `set urlacl`. Ele usa uma cadeia de caracteres que contém uma URL totalmente qualificada, que funciona como a chave do registro da reserva que está sendo feita.  
  
 O parâmetro `/a` também é obrigatório ao usar `set urlacl`. Ele usa uma cadeia de caracteres que contém uma ACL (lista de controle de acesso) na forma de uma cadeia de caracteres SDDL (Linguagem de Definição do Descritor de Segurança).  
  
 O seguinte é um exemplo de como usar esse comando.  
  
```  
httpcfg.exe set urlacl /u http://myhost:8000/ /a "O:AOG:DAD:(A;;RPWPCCDCLCSWRCWDWOGA;;;S-1-0-0)"  
```  
  
### <a name="running-windows-vista-windows-server-2008-r2-or-windows-7"></a>Executando o Windows Vista, o Windows Server 2008 R2 ou o Windows 7  
 Se você estiver executando no [!INCLUDE[wv](../../../../includes/wv-md.md)], no Windows Server 2008 R2 ou no Windows 7, use a ferramenta Netsh.exe. O seguinte é um exemplo de como usar esse comando.  
  
```  
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user  
```  
  
 Esse comando adiciona uma reserva de URL para o namespace da URL especificado no formato DOMÍNIO\conta de usuário.  Para obter mais informações sobre como usar o comando netsh, digite "netsh http add urlacl" em um prompt de comando e pressione inserir.  
  
## <a name="configuring-a-firewall-exception"></a>Configurando uma exceção do Firewall  
 Ao auto-hospedar um serviço WCF que se comunica por HTTP, uma exceção deverá ser adicionada à configuração do firewall para permitir conexões de entrada usando uma URL específica. Para obter mais informações, consulte [abrir uma porta no Firewall do Windows (Windows 7)](https://go.microsoft.com/fwlink/?LinkId=239961)  
  
## <a name="configuring-ssl-certificates"></a>Configurando certificados SSL  
 O protocolo SSL usa certificados no cliente e no servidor para armazenar as chaves de criptografia. O servidor fornece seu certificado SSL quando uma conexão é feita para que o cliente possa verificar a identidade do servidor. O servidor também pode solicitar um certificado do cliente para fornecer autenticação mútua dos dois lados da conexão.  
  
 Os certificados são armazenados em um repositório centralizado de acordo com o endereço IP e o número da porta de conexão. O endereço IP especial 0.0.0.0 corresponde a qualquer endereço IP do computador local. Observe que o repositório de certificados não faz distinção de URLs com base no caminho. Os serviços com a mesma combinação de endereço IP e porta devem compartilhar certificados mesmo que o caminho da URL dos serviços seja diferente.  
  
 Para obter instruções passo a passo, consulte [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="configuring-the-ip-listen-list"></a>Configurando a lista de escuta de IP  
 A API de servidor HTTP é associada apenas a um endereço IP e porta quando um usuário registra uma URL. Por padrão, a API de servidor HTTP é associada à porta na URL para todos os endereços IP do computador. Ocorrerá um conflito se um aplicativo, que não use a API de servidor HTTP, tiver sido associado anteriormente a essa combinação de endereço IP e porta. A lista de escuta de IP permite que os serviços do WCF coexistir com aplicativos que usam uma porta para alguns dos endereços IP da máquina. Se a lista de escuta IP contiver qualquer entrada, a API de servidor HTTP será associada apenas aos endereços IP especificados na lista. A modificação da lista de escuta IP exige privilégios administrativos.  
  
### <a name="running-windows-xp-or-server-2003"></a>Executando o Windows XP ou Server 2003  
 Use a ferramenta httpcfg para modificar a lista de escuta IP, conforme mostrado no exemplo a seguir. O [documentação de ferramentas de suporte do Windows](https://go.microsoft.com/fwlink/?LinkId=94840) explica a sintaxe da ferramenta httpcfg.exe.  
  
```  
httpcfg.exe set iplisten -i 0.0.0.0:8000  
```  
  
### <a name="running-windows-vista-or-windows-7"></a>Executando o Windows Vista ou o Windows 7  
 Use a ferramenta netsh para modificar a lista de escuta IP, conforme mostrado no exemplo a seguir.  
  
```  
netsh http add iplisten ipaddress=0.0.0.0:8000  
```  
  
## <a name="other-configuration-settings"></a>Outros parâmetros de configuração  
 Ao usar <xref:System.ServiceModel.WSDualHttpBinding>, a conexão de cliente usa os padrões que são compatíveis com as reservas de namespace e o firewall do Windows. Se você escolher personalizar o endereço base do cliente de uma conexão dupla, também deverá definir essas configurações HTTP no cliente para que correspondam ao novo endereço.  
  
 A API de servidor HTTP tem algumas configurações avançadas que não estão disponíveis por meio de HttpCfg. Essas configurações são mantidas no Registro e aplicam-se a todos os aplicativos executados nos sistemas que usam as APIs do servidor HTTP. Para obter informações sobre essas configurações, consulte [configurações de registro HTTP. sys para IIS](https://go.microsoft.com/fwlink/?LinkId=94843). A maioria dos usuários não precisa alterar essas configurações.  
  
## <a name="issues-specific-to-windows-xp"></a>Problemas específicos ao Windows XP  
 O IIS não oferece suporte ao compartilhamento de portas no [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Se o IIS está em execução e um serviço WCF tenta usar um namespace com a mesma porta, o serviço WCF não for iniciado. O IIS e WCF usam a porta 80 como padrão. Altere a atribuição de porta para um dos serviços ou use a lista de escuta de IP para atribuir o serviço WCF a um adaptador de rede não usado pelo IIS. O IIS 6.0 e posterior foi reprojetado para usar APIs do servidor HTTP.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.WSDualHttpBinding>  
 [Como configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
