---
title: Configurando HTTP e HTTPS - WCF
ms.date: 04/08/2019
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: 86705a4f8daa327c442ac6c53c9b44c5b5c5c2ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427169"
---
# <a name="configuring-http-and-https"></a>Configurando HTTP e HTTPS

Os serviços e os clientes WCF podem se comunicar por HTTP e HTTPS. As configurações de HTTP/HTTPS são definidas usando o IIS (Serviços de Informações da Internet) ou uma ferramenta de linha de comando. Quando um serviço WCF é hospedado no IIS HTTP ou HTTPS, as configurações podem ser definidas no IIS (usando a ferramenta inetmgr.exe). Se um serviço WCF for auto-hospedado, as configurações de HTTP ou HTTPS serão definidas usando uma ferramenta de linha de comando.

No mínimo, você deseja configurar um registro de URL e adicionar uma exceção de Firewall para a URL usando o seu serviço. Você pode definir essas configurações com a ferramenta Netsh.exe.

## <a name="configuring-namespace-reservations"></a>Configurando reservas de namespace

A reserva de namespace atribui os direitos para uma parte do namespace da URL HTTP para um determinado grupo de usuários. Uma reserva dá a esses usuários o direito de criar serviços que escutam naquela parte do namespace. As reservas são prefixos de URL, que significa que a reserva cobre todos os subcaminhos do caminho de reserva. As reservas de namespace permitem usar caracteres curinga de duas maneiras. A documentação da API de servidor HTTP descreve a [ordem de resolução de nomes entre as declarações de namespace que envolvem caracteres curinga](/windows/desktop/Http/routing-incoming-requests).

Um aplicativo em execução pode criar uma solicitação semelhante para adicionar registros de namespace. Os registros e as reservas competem por partes do namespace. Uma reserva pode ter precedência sobre um registro de acordo com a ordem de resolução determinada na [ordem de resolução de nomes entre as declarações de namespace que envolvem caracteres curinga](/windows/desktop/Http/routing-incoming-requests). Nesse caso, a reserva impede que o aplicativo em execução receba pedidos.

O exemplo a seguir usa a ferramenta Netsh.exe:

```console
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user
```

Este comando adiciona uma reserva de URL para o namespace de URL especificado para a conta de domínio \ usuário. Para obter mais informações sobre como usar o comando netsh, digite `netsh http add urlacl /?` em um prompt de comando e pressione Enter.

## <a name="configuring-a-firewall-exception"></a>Configurando uma exceção de firewall

Ao auto-hospedar um serviço WCF que se comunica por HTTP, uma exceção deverá ser adicionada à configuração do firewall para permitir conexões de entrada usando uma URL específica.

## <a name="configuring-ssl-certificates"></a>Configurar certificados SSL

O protocolo SSL usa certificados no cliente e no servidor para armazenar as chaves de criptografia. O servidor fornece seu certificado SSL quando uma conexão é feita para que o cliente possa verificar a identidade do servidor. O servidor também pode solicitar um certificado do cliente para fornecer autenticação mútua dos dois lados da conexão.

Os certificados são armazenados em um repositório centralizado de acordo com o endereço IP e o número da porta de conexão. O endereço IP especial 0.0.0.0 corresponde a qualquer endereço IP do computador local. Observe que o repositório de certificados não distingue URLs com base no caminho. Os serviços com a mesma combinação de endereço IP e porta devem compartilhar certificados mesmo que o caminho da URL dos serviços seja diferente.

Para obter instruções passo a passo, consulte [como: Configurar uma porta com um certificado SSL](how-to-configure-a-port-with-an-ssl-certificate.md).

## <a name="configuring-the-ip-listen-list"></a>Configurando a lista de escuta de IP

A API de servidor HTTP é associada apenas a um endereço IP e porta quando um usuário registra uma URL. Por padrão, a API de servidor HTTP é associada à porta na URL para todos os endereços IP do computador. Um conflito será gerado se um aplicativo que não usa o HTTP Server API tiver sido associado anteriormente a essa combinação de endereço IP e porta. A lista de escuta de IP permite que os serviços do WCF coexistir com aplicativos que usam uma porta para alguns dos endereços IP da máquina. Se a lista de escuta IP contiver qualquer entrada, a API de servidor HTTP será associada apenas aos endereços IP especificados na lista. A modificação da lista de escuta IP exige privilégios administrativos.

Use a ferramenta netsh para modificar a lista de escuta de IP, conforme mostrado no exemplo a seguir:

```console
netsh http add iplisten ipaddress=0.0.0.0:8000
```

## <a name="other-configuration-settings"></a>Outras definições de configuração

Ao usar <xref:System.ServiceModel.WSDualHttpBinding>, a conexão de cliente usa os padrões que são compatíveis com as reservas de namespace e o firewall do Windows. Se você escolher personalizar o endereço base do cliente de uma conexão dupla, também deverá definir essas configurações HTTP no cliente para que correspondam ao novo endereço.

A API do servidor HTTP tem algumas configurações avançadas que não estão disponíveis por meio de HttpCfg. Essas configurações são mantidas no Registro e aplicam-se a todos os aplicativos executados nos sistemas que usam as APIs do servidor HTTP. Para obter informações sobre essas configurações, consulte [configurações de registro HTTP. sys para IIS](https://support.microsoft.com/en-us/help/820129/http-sys-registry-settings-for-windows). A maioria dos usuários não precisa alterar essas configurações.

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.WSDualHttpBinding>
- [Como: Configurar uma porta com um certificado SSL](how-to-configure-a-port-with-an-ssl-certificate.md)
