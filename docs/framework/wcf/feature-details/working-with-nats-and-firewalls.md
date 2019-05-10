---
title: Trabalhando com NATs e firewalls
ms.date: 03/30/2017
helpviewer_keywords:
- firewalls [WCF]
- NATs [WCF]
ms.assetid: 74db0632-1bf0-428b-89c8-bd53b64332e7
ms.openlocfilehash: 5415fc173be10834f73b5959481951407bcee0b1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637335"
---
# <a name="working-with-nats-and-firewalls"></a>Trabalhando com NATs e firewalls
O cliente e o servidor de uma conexão de rede com frequência não têm uma conexão direta e abrir o caminho para a comunicação. Pacotes são filtradas, roteadas, analisados e transformados em máquinas de ponto de extremidade e pelas máquinas intermediárias na rede. Conversões de endereço de rede (NATs) e firewalls são exemplos comuns de aplicativos intermediários que podem participar da comunicação de rede.  
  
 Transportes do Windows Communication Foundation (WCF) e (MEPs) de padrões de troca de mensagem diferente para, reagem a presença de NATs e firewalls. Este tópico descreve como NATs e firewalls funcionam em comum topologias de rede. Recomendações para combinações específicas de transportes WCF e MEPs recebem que ajudam a tornar seus aplicativos mais robustos para NATs e firewalls na rede.  
  
## <a name="how-nats-affect-communication"></a>Como NATs afetam a comunicação  
 NAT foi criado para permitir que vários computadores compartilhar um único endereço IP externo. Um NAT remapeamento de porta mapeia um endereço IP interno e a porta para uma conexão para um endereço IP externo com um novo número de porta. O novo número de porta permite que o NAT correlacionar o tráfego de retorno com a comunicação original. Muitos usuários domésticos agora tem um endereço IP que só pode ser roteado em particular e dependem de um NAT para fornecer roteamento global de pacotes.  
  
 Um NAT não fornece um limite de segurança. No entanto, configurações comuns da NAT impedir que os computadores internos que está sendo abordado diretamente. Isso protege as máquinas internas de algumas conexões indesejadas tanto torna difícil escrever aplicativos de servidor que devem enviar dados de volta para o cliente de forma assíncrona. O NAT reconfigura os endereços em pacotes para torná-lo parecer que as conexões são originária de computador NAT. Isso faz com que o servidor falhe quando ele tenta abrir uma conexão volta ao cliente. Se o servidor usa o endereço do cliente percebido, ele falhará porque o endereço do cliente não pode ser roteado publicamente. Se o servidor usa o endereço NAT, ele não conseguir se conectar, pois nenhum aplicativo está escutando nessa máquina.  
  
 Alguns NATs suportam à configuração das regras para permitir que computadores externos para se conectar a um determinado computador interno de encaminhamento. As instruções para configurar regras de encaminhamento varia entre diferentes NATs e pedir aos usuários finais para alterar sua configuração de NAT não é recomendado para a maioria dos aplicativos. Muitos usuários finais não pode ou não quiser alterar sua configuração de NAT para um aplicativo específico.  
  
## <a name="how-firewalls-affect-communication"></a>Como Firewalls afetam a comunicação  
 Um *firewall* é um dispositivo de hardware ou software que aplica regras para o tráfego que passa por meio de decidir se deseja permitir ou negar a passagem. Você pode configurar firewalls para examinar os fluxos de entrada e/ou saídos de tráfego. O firewall fornece um limite de segurança para a rede da borda da rede ou no host do ponto de extremidade. Tradicionalmente, os usuários empresariais manteve seus servidores atrás de um firewall para impedir ataques mal-intencionados. Desde a introdução do firewall pessoal em [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], o número de usuários domésticos atrás de um firewall aumentou muito bem. Assim, é provável que uma ou ambas as extremidades de uma conexão tem um firewall examinando os pacotes.  
  
 Firewalls variam muito em termos de sua complexidade e a capacidade para examinar pacotes. Firewalls simples aplicam regras com base em como os endereços de origem e de destino e portas em pacotes. Firewalls inteligentes também podem examinar o conteúdo dos pacotes para tomar decisões. Esses firewalls são fornecidos em muitas configurações diferentes e geralmente são usadas para aplicativos especializados.  
  
 É uma configuração comum para um firewall de usuário doméstico proibir as conexões de entrada, a menos que uma conexão de saída foi feita a essa máquina anteriormente. É uma configuração comum para um firewall de usuário de negócios proibir as conexões de entrada em todas as portas, exceto um grupo especificamente identificado. Um exemplo é um firewall que proíbe a conexões em todas as portas, exceto as portas 80 e 443 para fornecer serviço HTTP e HTTPS. Firewalls gerenciados existem para usuários domésticos e de negócios que permitem a um usuário confiável ou processo no computador para alterar a configuração do firewall. Firewalls gerenciados são mais comuns para usuários domésticos onde não há nenhuma política corporativa controlando o uso de rede.  
  
## <a name="using-teredo"></a>Usando Teredo  
 Teredo é uma tecnologia de transição IPv6 que permite que a capacidade de endereçamento direta das máquinas por trás de um NAT. Teredo se baseia no uso de um servidor que pode ser publicamente e globalmente roteado para anunciar conexões potenciais. O servidor Teredo oferece o aplicativo cliente e servidor um ponto de reunião comum no qual eles podem trocar informações de conexão. As máquinas, em seguida, solicitem um endereço de Teredo temporário e pacotes são encapsulados por meio da rede existente. Suporte de Teredo no WCF requer habilitar o suporte a IPv6 e Teredo no sistema operacional. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] e sistemas operacionais posteriores dão suporte a Teredo. [!INCLUDE[wv](../../../../includes/wv-md.md)] e sistemas operacionais posteriores dão suporte ao IPv6 por padrão e exige apenas que o usuário habilitar o Teredo. [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] e [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] exigem que o usuário habilitar o IPv6 e Teredo. Para obter mais informações, consulte o [visão geral do Teredo](https://go.microsoft.com/fwlink/?LinkId=87571).  
  
## <a name="choosing-a-transport-and-message-exchange-pattern"></a>Escolhendo um transporte e padrões de troca de mensagem  
 Selecionando um transporte e MEP é um processo de três etapas:  
  
1. Analise a capacidade de endereçamento das máquinas de ponto de extremidade. Servidores corporativos normalmente têm a capacidade de endereçamento direta, enquanto os usuários finais normalmente têm sua capacidade de endereçamento bloqueada por NATs. Se ambos os pontos de extremidade protegido por um NAT, como em cenários de ponto a ponto entre os usuários finais, em seguida, talvez seja necessário uma tecnologia, como a Teredo para fornecer capacidade de endereçamento.  
  
2. Analise as restrições de porta e protocolo as máquinas de ponto de extremidade. Servidores corporativos normalmente estão atrás de firewalls de alta seguras que bloqueiam muitas portas. No entanto, a porta 80 é aberta com frequência para permitir o tráfego HTTP e porta 443 está aberta para permitir o tráfego HTTPS. Os usuários finais têm menor probabilidade de ter restrições de porta, mas pode ser protegido por um firewall que permite apenas conexões de saída. Alguns firewalls permitem o gerenciamento por aplicativos no ponto de extremidade para abrir as conexões de forma seletiva.  
  
3. Computação de transportes e MEPs permitem que as restrições de capacidade de endereçamento e a porta de rede.  
  
 Uma topologia comuns para aplicativos cliente-servidor é que os clientes que estão atrás de um NAT sem Teredo com um firewall apenas de saída e um servidor que está diretamente endereçável com um firewall de alta segurança. Neste cenário, o transporte TCP com um MEP duplex e um transporte HTTP com uma solicitação-resposta MEP funcionar muito bem. Uma topologia comuns para aplicativos ponto a ponto é que ambos os pontos de extremidade atrás de NATs e firewalls. Nesse cenário e em cenários em que a topologia de rede é desconhecida, considere as seguintes recomendações:  
  
- Não use transportes duplos. Um transporte duplo abre mais conexões, o que reduz as chances de se conectar com êxito.  
  
- Suporte a estabelecer canais de back sobre a conexão de origem. Usar back canais, como em TCP/IP duplex, abre menos conexões, o que aumenta as chances de se conectar com êxito.  
  
- Emprega um serviço acessível para registrar pontos de extremidade ou retransmitir o tráfego. Usando um serviço de conexão pode ser acessado globalmente, como um servidor Teredo, aumenta a chance de se conectar com êxito quando a topologia de rede é restritiva ou desconhecido.  
  
 As tabelas a seguir examinam o unidirecional, solicitação-resposta e duplex MEPs e TCP padrão, TCP com Teredo, e os transportes de HTTP padrão e dupla no WCF.  
  
|Capacidade de endereçamento|Direto de servidor|Servidor direto com NAT traversal|Servidor NAT|Servidor NAT com NAT traversal|  
|--------------------|-------------------|--------------------------------------|----------------|-----------------------------------|  
|Cliente direto|Qualquer transporte e MEP|Qualquer transporte e MEP|Sem suporte.|Sem suporte.|  
|Cliente direto com NAT traversal|Qualquer transporte e MEP.|Qualquer transporte e MEP.|Sem suporte.|TCP com Teredo e qualquer MEP. [!INCLUDE[wv](../../../../includes/wv-md.md)] tem uma opção de configuração de todo o computador para o suporte HTTP com Teredo.|  
|Cliente NAT|Qualquer transporte não duplo e MEP. Duplex MEP requer o transporte TCP.|Qualquer transporte não duplo e MEP. Duplex MEP requer o transporte TCP.|Sem suporte.|Sem suporte.|  
|Cliente NAT com NAT traversal|Qualquer transporte não duplo e MEP. Duplex MEP requer o transporte TCP.|HTTP duplo de tudo, exceto e qualquer MEP. Duplex MEP requer o transporte TCP. Transporte TCP duplo requer Teredo. [!INCLUDE[wv](../../../../includes/wv-md.md)] tem uma opção de configuração de todo o computador para o suporte HTTP com Teredo.|Sem suporte.|TCP com Teredo e qualquer MEP. [!INCLUDE[wv](../../../../includes/wv-md.md)] tem uma opção de configuração de todo o computador para o suporte HTTP com Teredo.|  
  
|Restrições de firewall|Abrir do servidor|Servidor com o firewall gerenciado|Servidor com o firewall somente HTTP|Servidor com o firewall apenas de saída|  
|---------------------------|-----------------|----------------------------------|-------------------------------------|-----------------------------------------|  
|Abrir do cliente|Qualquer transporte e MEP.|Qualquer transporte e MEP.|Qualquer transporte HTTP e MEP.|Sem suporte.|  
|Cliente com o firewall gerenciado|Qualquer transporte não duplo e MEP. Duplex MEP requer o transporte TCP.|Qualquer transporte não duplo e MEP. Duplex MEP requer o transporte TCP.|Qualquer transporte HTTP e MEP.|Sem suporte.|  
|Cliente com o firewall somente HTTP|Qualquer transporte HTTP e MEP.|Qualquer transporte HTTP e MEP.|Qualquer transporte HTTP e MEP.|Sem suporte.|  
|Cliente com o firewall apenas de saída|Qualquer transporte não duplo e MEP. Duplex MEP requer o transporte TCP.|Qualquer transporte não duplo e MEP. Duplex MEP requer o transporte TCP.|Qualquer transporte HTTP e qualquer MEP de não-duplex.|Sem suporte.|
