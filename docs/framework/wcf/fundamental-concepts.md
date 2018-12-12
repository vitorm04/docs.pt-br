---
title: Conceitos fundamentais do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], concepts
- concepts [WCF]
- fundamentals [WCF]
- Windows Communication Foundation [WCF], concepts
ms.assetid: 3e7e0afd-7913-499d-bafb-eac7caacbc7a
ms.openlocfilehash: 9957b937dd59f82a5d1962fee33593d7a0c1b7c1
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286553"
---
# <a name="fundamental-windows-communication-foundation-concepts"></a>Conceitos fundamentais do Windows Communication Foundation
Este documento fornece uma visão geral da arquitetura do Windows Communication Foundation (WCF). Ele destina-se a explicar os principais conceitos e como eles se adaptam entre si. Para obter um tutorial sobre como criar a versão mais simples de um serviço WCF e um cliente, consulte [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md). Para aprender a programação de WCF, consulte [programação WCF básica](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="wcf-fundamentals"></a>Princípios básicos do WCF  
 WCF é um tempo de execução e um conjunto de APIs para a criação de sistemas que enviam mensagens entre serviços e clientes. A mesma infraestrutura e APIs são usados para criar aplicativos que se comunicam com outros aplicativos no mesmo sistema de computador ou em um sistema que reside em outra empresa e é acessado pela Internet.  
  
### <a name="messaging-and-endpoints"></a>Mensagem e pontos de extremidade  
 WCF baseia-se na noção de comunicação baseada em mensagem e qualquer coisa que pode ser modelada como uma mensagem (por exemplo, uma solicitação HTTP ou uma mensagem de enfileiramento de mensagens (também conhecido como MSMQ)) pode ser representada de maneira uniforme no modelo de programação. Isso permite uma API unificada em mecanismos de transporte diferentes.  
  
 O modelo faz distinção entre *clientes*, que são aplicativos que iniciam a comunicação, e *services*, que são aplicativos que esperam que os clientes para se comunicar com eles e responder a que comunicação. Um único aplicativo pode atuar como um cliente e um serviço. Para obter exemplos, consulte [serviços Duplex](../../../docs/framework/wcf/feature-details/duplex-services.md) e [Peer-to-Peer Networking](../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 As mensagens são enviadas entre pontos de extremidade. *Pontos de extremidade* são locais onde as mensagens são enviadas ou recebidas (ou ambos) e definem todas as informações necessárias para a troca de mensagens. Um serviço expõe um ou mais pontos de extremidade do aplicativo (assim como zero ou mais pontos de extremidade de infraestrutura) e o cliente gera um ponto de extremidade que é compatível com um dos pontos de extremidade do serviço.  
  
 Uma *ponto de extremidade* descreve de maneira baseado em padrões onde as mensagens devem ser enviadas, como deve ser enviadas e o que devem ser a aparência de mensagens. Um serviço pode expor essas informações como metadados que os clientes podem processar para gerar clientes apropriados do WCF e comunicação *pilhas*.  
  
### <a name="communication-protocols"></a>Protocolos de comunicação  
 Um elemento necessário da pilha de comunicação é o *protocolo de transporte*. As mensagens podem ser enviados pela Internet e por intranets usando transportes comuns, como HTTP e TCP. Estão incluídos outros transportes que dão suporte à comunicação com aplicativos de Enfileiramento de Mensagens e nós em uma malha de rede par. Mais mecanismos de transporte podem ser adicionados usando os pontos de extensão internos do WCF.  
  
 Outro elemento necessário na pilha de comunicação é a codificação que especifica como qualquer mensagem determinada é formatada. O WCF fornece as seguintes codificações:  
  
-   Codificação de texto, uma codificação interoperável.  
  
-   Codificação MTOM (Mecanismo de otimização de transmissão de mensagens), que é uma maneira interoperável de enviar com eficiência dados binários não estruturados para e de um serviço.  
  
-   Codificação binária para a transferência eficiente.  
  
 Mais mecanismos de codificação (por exemplo, uma codificação de compactação) podem ser adicionados usando os pontos de extensão internos do WCF.  
  
### <a name="message-patterns"></a>Padrões de mensagem  
 O WCF oferece suporte a vários padrões de mensagens, incluindo a solicitação-resposta, unidirecional e comunicação duplex. Os transportes diferentes dão suporte a padrões diferentes de mensagem e, portanto, afetam os tipos de interações que eles suportam. As APIs do WCF e o tempo de execução também ajudarão-lo para enviar mensagens de maneira segura e confiável.  
  
## <a name="wcf-terms"></a>Termos do WCF  
 Outros conceitos e termos usados na documentação do WCF incluem o seguinte.  
  
 mensagem  
 Uma unidade independente de dados que pode ser formada por várias partes, incluindo um corpo e cabeçalhos.  
  
 serviço  
 Uma construção que expõe um ou mais pontos de extremidade, com cada ponto de extremidade expondo uma ou mais operações de serviço.  
  
 ponto de extremidade  
 Uma construção na qual as mensagens são enviadas ou recebidas (ou ambos). Ele consiste em um local (um endereço) que define onde as mensagens podem ser enviadas, uma especificação do mecanismo de comunicação (uma associação) que descreve como as mensagens devem ser enviadas, e uma definição para um conjunto de mensagens que podem ser enviadas ou recebidas (ou ambos) em que local (um contrato de serviço) que descreve qual mensagem pode ser enviada.  
  
 Um serviço WCF é exposto ao mundo como uma coleção de pontos de extremidade.  
  
 ponto de extremidade do aplicativo  
 Um ponto de extremidade exposto pelo aplicativo e que corresponde a um contrato de serviço implementado pelo aplicativo.  
  
 ponto de extremidade de infraestrutura  
 Um ponto de extremidade que é exposto pela infraestrutura para facilitar a funcionalidade que é necessária ou fornecida pelo serviço que não está relacionado a um contrato de serviço. Por exemplo, um serviço pode ter um ponto de extremidade de infraestrutura que fornece informações de metadados.  
  
 endereço  
 Especifica o local onde as mensagens são recebidas. É especificado como um URI (Uniform Resource Identifier). A parte do esquema URI nomeia o mecanismo de transporte a ser usado para alcançar o endereço, por exemplo, HTTP e TCP. A parte hierárquica do URI contém um local exclusivo cujo formato é dependente do mecanismo de transporte.  
  
 O endereço do ponto de extremidade permite que você crie endereços exclusivos de ponto de extremidade para cada ponto de extremidade em um serviço, ou, sob determinadas condições, para compartilhar um endereço através de pontos de extremidade. O exemplo a seguir mostra um endereço usando o protocolo HTTPS com uma porta não padrão:  
  
```  
HTTPS://cohowinery:8005/ServiceModelSamples/CalculatorService  
```  
  
 associação  
 Define como um ponto de extremidade comunica-se com o mundo. Ele é construído de um conjunto de componentes chamados elementos de associação que “empilham” um sobre o outro para criar a infraestrutura de comunicação. No mínimo, uma associação define o transporte (como HTTP ou TCP) e a codificação que está sendo usada (como texto ou binário). Uma associação pode conter elementos de associação que especificam detalhes como mecanismos de segurança usados para proteger mensagens, ou o padrão de mensagem usado por um ponto de extremidade. Para obter mais informações, consulte [Configurando os serviços de](../../../docs/framework/wcf/configuring-services.md).  
  
 elemento de associação  
 Representa uma parte específica da associação, como um transporte, uma codificação, uma implementação de um protocolo de nível de infraestrutura (como WS-ReliableMessaging), ou qualquer outro componente da pilha de comunicação.  
  
 comportamentos  
 Um componente que controla vários aspectos de tempo de execução de um serviço, um ponto de extremidade, uma operação específico ou um cliente. Os comportamentos são agrupados de acordo com o escopo: os comportamentos comuns afetam todos os pontos de extremidade globalmente, os aspectos de serviço afetam somente aspectos relacionados a serviço, os comportamentos de ponto de extremidade afetam somente as propriedades relacionadas a ponto de extremidade e os comportamentos de nível de operação afetam operações específicas. Por exemplo, um comportamento do serviço é a limitação, que especifica como um serviço reage quando um excesso de mensagens ameaça sobrecarregar seus recursos de manipulação. Um comportamento de ponto de extremidade, por outro lado, controla somente os aspectos que são relevantes para os pontos de extremidade, por exemplo, como e onde localizar uma credencial de segurança.  
  
 associações fornecidas pelo sistema  
 WCF inclui um número o sistema forneceu associações. Essas são coleções de elementos de associação que são otimizados para cenários específicos. Por exemplo, o <xref:System.ServiceModel.WSHttpBinding> é criado para proporcionar a interoperabilidade com serviços que implementam várias especificações de WS-*. Essas associações predefinidas economizam tempo apresentando somente essas opções que podem ser corretamente aplicadas ao cenário específico. Se uma associação predefinida não atender aos requisitos, você poderá criar sua própria associação personalizada.  
  
 configuração versus codificação  
 O controle de um aplicativo pode ser feito por meio de codificação, configuração ou uma combinação de ambos. A configuração tem a vantagem de permitir que alguém que não seja o desenvolvedor (por exemplo, um administrador de rede) defina o cliente e os parâmetros de serviço após o código ser escrito e sem ter que recompilar. A configuração permite que você não apenas defina os valores como endereços de ponto de extremidade, mas também permite um controle adicional para adicionar pontos de extremidade, associações e comportamentos. A codificação permite que o desenvolvedor mantenha o controle restrito sobre todos os componentes de serviço ou cliente, e as configurações feitas podem ser inspecionadas e, se necessário, substituídas pelo código.  
  
 operação de serviço  
 Um procedimento definido no código de um serviço que implementa a funcionalidade para uma operação. Esta operação é exposto aos clientes como métodos em um cliente do windows. O método pode retornar um valor e pode utilizar um número opcional de argumentos, ou não utilizar argumentos, e não retornar nenhuma resposta. Por exemplo, uma operação que funciona como um simples “Hello” pode ser usada como uma notificação da presença de um cliente e iniciar uma série de operações.  
  
 contrato de serviço  
 Agrupa várias operações relacionadas em uma única unidade funcional. O contrato pode definir configurações de nível de serviço, como o namespace do serviço, um contrato correspondente de retorno de chamada e outras configurações semelhantes. Na maioria dos casos, o contrato é definido criando uma interface na linguagem de programação de sua escolha e aplicando o atributo <xref:System.ServiceModel.ServiceContractAttribute> à interface. O código real do serviço é gerado implementando a interface.  
  
 contrato de operação  
 Um contrato de operação define os parâmetros e o tipo de retorno de uma operação. Ao criar uma interface que define o contrato de serviço, você significa um contrato de operação aplicando o atributo <xref:System.ServiceModel.OperationContractAttribute> a cada definição do método que faz parte do contrato. As operações podem ser modeladas como utilizar uma única mensagem e retornar uma única mensagem, ou como utilizar um conjunto de tipos e retornar um tipo. Nesse último caso, o sistema determinará o formato das mensagens que precisam ser trocadas para essa operação.  
  
 contrato de mensagens  
 Descreve o formato de uma mensagem. Por exemplo, isso declara se os elementos da mensagem devem estar presentes em cabeçalhos ou no corpo, qual nível de segurança deve ser aplicado para quais elementos de mensagem e assim por diante.  
  
 contrato de falha  
 Pode estar associado com uma operação de serviço para denotar os erros que podem ser retornados para o chamador. Uma operação pode ter zero ou mais falhas associadas a ela. Esses erros são falhas SOAP que são modeladas como exceções no modelo de programação.  
  
 contrato de dados  
 As descrições nos metadados dos tipos de dados que um serviço usa. Isso permite que outros interoperem com o serviço. Os tipos de dados podem ser usados em qualquer parte de uma mensagem, por exemplo, como parâmetros ou tipos de retorno. Se o serviço estiver usando somente tipos simples, não há necessidade de usar explicitamente contratos de dados.  
  
 hospedagem  
 Um serviço deve ser hospedado em algum processo. Um *host* é um aplicativo que controla o tempo de vida do serviço. Os serviços podem ser auto-hospedados ou gerenciados por um processo de hospedagem existente.  
  
 serviço auto-hospedado  
 Um serviço que é executado dentro de um aplicativo de processo que o desenvolvedor criou. O desenvolvedor controla o tempo de vida, define as propriedades do serviço, abre o serviço (que o define em um modo escuta) e fecha o serviço.  
  
 processo de hospedagem  
 Um aplicativo que é criado para hospedar serviços. São eles: IIS (Serviços de Informações da Internet), WAS (Serviços de Ativação do Windows) e Serviços do Windows. Nesses cenários hospedados, o host controla o tempo de vida do serviço. Por exemplo, usando o IIS, você pode configurar um diretório virtual que contém o assembly do serviço e o arquivo de configuração. Quando uma mensagem é recebida, o IIS inicia o serviço e controla o tempo de vida.  
  
 instanciação  
 Um serviço tem um modelo de instanciação. Há três modelos de instanciação: “simples”, no qual um único objeto CLR atende a todos os clientes; “por chamada”, no qual um novo objeto CLR é criado para manipular cada chamada de cliente; e “por sessão” no qual um conjunto de objetos CLR é criado, um para cada sessão separada. A escolha de um modelo de instanciação depende dos requisitos de aplicativo e o padrão de uso esperado do serviço.  
  
 aplicativo cliente  
 Um programa que troca mensagens com um ou mais pontos de extremidade. O aplicativo cliente começa criando uma instância de um cliente de WCF e chamando métodos de cliente do windows. É importante observar que um único aplicativo pode ser um cliente e um serviço.  
  
 canal  
 Uma implementação concreta de um elemento de associação. A associação representa a configuração e o canal é a implementação associada com essa configuração. Portanto, há um canal associado com cada elemento de associação. O canais empilham-se uns sobre os outros para criar a implementação concreta da associação: a pilha do canal.  
  
 Cliente de WCF  
 Uma construção de aplicativo cliente que expõe as operações de serviço como métodos (na linguagem de programação de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] de sua escolha, como Visual Basic ou Visual C#). Qualquer aplicativo pode hospedar um cliente de WCF, incluindo um aplicativo que hospeda um serviço. Portanto, é possível criar um serviço que inclui clientes de WCF de outros serviços.  
  
 Um cliente WCF pode ser automaticamente gerado usando o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) e apontá-lo em um serviço em execução que publica metadados.  
  
 metadados  
 Em um serviço, descreve as características do serviço que uma entidade externa precisa entender para se comunicar com o serviço. Os metadados podem ser consumidos pela [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar um cliente WCF e a configuração de rastreamento que um aplicativo cliente pode usar para interagir com o serviço.  
  
 Os metadados expostos pelo serviço incluem os documentos XML do esquema, que definem o contrato de dados do serviço, e os documentos WSDL, que descrevem os métodos do serviço.  
  
 Quando ativados, os metadados para o serviço são gerados automaticamente pela inspecionando o serviço e seus pontos de extremidade. Para publicar metadados de um serviço, você deverá explicitamente ativar o comportamento dos metadados.  
  
 segurança  
 No WCF, inclui confidencialidade (criptografia de mensagens para evitar bisbilhotar), integridade (os meios para detecção de violação da mensagem), (os meios para validação de servidores e clientes) de autenticação e autorização (o controle de acesso a recursos). Essas funções são fornecidas aproveitando os mecanismos de segurança existentes, como TLS sobre HTTP (também conhecido como HTTPS), ou implementando uma ou mais das várias especificações de segurança de WS-*.  
  
 modo de segurança de transporte  
 Especifica que a confidencialidade, a integridade e a autenticação são fornecidas pelos mecanismos da camada de transporte (como HTTPS). Ao usar um transporte como HTTPS, esse modo tem a vantagem de ser eficiente no desempenho, além de bem-compreendido devido à sua predominância na Internet. A desvantagem é que esse tipo de segurança é aplicado separadamente em cada salto no caminho de comunicação, tornando a comunicação suscetível a um ataque de intermediários.  
  
 modo de segurança de mensagem  
 Especifica que a segurança é fornecida implementando uma ou mais das especificações de segurança, como a especificação denominada [Web Services Security: Segurança de mensagem SOAP](https://go.microsoft.com/fwlink/?LinkId=94684). Cada mensagem contém os mecanismos necessários para fornecer segurança durante seu trânsito e ativar os destinatários para detectar violação e descriptografar as mensagens. Nesse sentido, a segurança é encapsulada dentro de cada mensagem, fornecendo segurança de ponta a ponta em vários saltos. Como as informações de segurança se tornam parte da mensagem, também é possível incluir vários tipos de credenciais com a mensagem (elas são denominadas *declarações*). Essa abordagem também tem a vantagem de permitir que a mensagem viaje com segurança em qualquer transporte, incluindo vários transportes entre sua origem e o destino. A desvantagem dessa abordagem é a complexidade dos mecanismos de criptografia empregados, resultando em implicações de desempenho.  
  
 transporte com modo de segurança de credencial de mensagem  
 Especifica o uso da camada de transporte para fornecer confidencialidade, autenticação e integridade de mensagens, embora cada uma das mensagens possa conter várias credenciais (reivindicações) exigidas pelos destinatários da mensagem.  
  
 WS-*  
 Taquigrafia para o conjunto crescente de especificações de (WS) de serviço Web, como WS- segurança, WS - ReliableMessaging, e assim por diante, que são implementadas em windows.  
  
## <a name="see-also"></a>Consulte também  
 [O que é o Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Arquitetura do Windows Communication Foundation](../../../docs/framework/wcf/architecture.md)  
 [Arquitetura de segurança](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
