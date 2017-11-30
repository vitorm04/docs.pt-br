---
title: Trabalhando com NATs e firewalls
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- firewalls [WCF]
- NATs [WCF]
ms.assetid: 74db0632-1bf0-428b-89c8-bd53b64332e7
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8fd5058179d9e7974e725d69bb2bf0740ab7f00
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-nats-and-firewalls"></a>Trabalhando com NATs e firewalls
O cliente e o servidor de uma conexão de rede com frequência não têm uma conexão direta e abrir o caminho para a comunicação. Pacotes são filtradas, roteadas, analisados e transformados em máquinas de ponto de extremidade e intermediários máquinas na rede. Conversões de endereço de rede (NAT) e firewalls são exemplos comuns de aplicativos intermediários que podem participar de comunicação de rede.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]transportes e (MEPs) de padrões de troca de mensagem diferente de reagem a presença de NATs e firewalls. Este tópico descreve como NATs e firewalls funcionam em comum topologias de rede. Recomendações para combinações específicas de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transportes e MEPs recebem que ajuda a tornar seus aplicativos mais robustos NATs e firewalls na rede.  
  
## <a name="how-nats-affect-communication"></a>Como NATs afetam a comunicação  
 NAT foi criado para permitir que várias máquinas compartilhar um único endereço IP externo. O remapeamento de porta NAT mapeia um endereço IP interno e a porta para uma conexão para um endereço IP externo com um novo número de porta. O novo número de porta permite o NAT correlacionar o tráfego de retorno com a comunicação original. Muitos usuários domésticos agora têm um endereço IP só é roteável em particular e dependem de um NAT para fornecer roteamento global de pacotes.  
  
 NAT não fornece um limite de segurança. No entanto, configurações comuns do NAT impedir as máquinas internas que é endereçado diretamente. Isso protege as máquinas internas de algumas conexões indesejados tanto dificulta a gravar aplicativos de servidor que assincronamente devem enviar dados de volta ao cliente. O NAT reconfigura os endereços em pacotes para torná-lo parecer conexões são provenientes de máquina NAT. Isso faz com que o servidor falha ao tentar abrir uma conexão para o cliente. Se o servidor usa o endereço do cliente percebido, ele falha porque o endereço do cliente não pode ser roteado publicamente. Se o servidor usa o endereço NAT, ele não consegue se conectar porque nenhum aplicativo está escutando nesse computador.  
  
 Alguns NATs oferece suporte à configuração de regras para permitir que computadores externos para se conectar a um determinado computador interno de encaminhamento. Varia de acordo com as instruções para configurar regras de encaminhamento entre diferentes NATs e pedir que os usuários finais para alterar suas configurações de NAT não é recomendado para a maioria dos aplicativos. Muitos usuários finais não pode ou não desejar alterar sua configuração de NAT para um aplicativo específico.  
  
## <a name="how-firewalls-affect-communication"></a>Como os Firewalls afetam a comunicação  
 Um *firewall* é um dispositivo de hardware ou software que aplica regras para o tráfego que passa para decidir se deseja permitir ou negar passagem. Você pode configurar os firewalls para examinar os fluxos de entrada e/ou saídos de tráfego. O firewall fornece um limite de segurança para a rede da borda da rede ou no host do ponto de extremidade. Os usuários empresariais tradicionalmente manteve seus servidores atrás de um firewall para impedir ataques mal-intencionados. Desde a introdução do firewall pessoal no [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], o número de usuários domésticos atrás de um firewall aumentou muito bem. Isso torna provável que uma ou ambas as extremidades de uma conexão tem um firewall examinando os pacotes.  
  
 Firewalls variam em termos de sua complexidade e a capacidade de examinar os pacotes. Firewalls simples aplicam regras com base em endereços de origem e de destino e portas em pacotes. Firewalls inteligentes também podem examinar o conteúdo dos pacotes para tomar decisões. Esses firewalls são fornecidos em muitas configurações diferentes e geralmente são usados para aplicativos especializados.  
  
 Uma configuração comum de um firewall de usuário inicial é proíbem conexões de entrada, a menos que uma conexão de saída foi feita a essa máquina anteriormente. Uma configuração comum de um firewall de usuário de negócios é proíbem conexões de entrada em todas as portas, exceto um grupo especificamente identificado. Um exemplo é um firewall que impede conexões em todas as portas, exceto as portas 80 e 443 para fornecer o serviço HTTP e HTTPS. Firewalls gerenciados existem para usuários domésticos e de negócios que permite que um usuário confiável ou um processo no computador para alterar a configuração de firewall. Firewalls gerenciados são mais comuns para usuários domésticos onde não há nenhuma política corporativa controlando o uso de rede.  
  
## <a name="using-teredo"></a>Usando o Teredo  
 Teredo é uma tecnologia de transição IPv6 que permite que o endereçamento direto de máquinas por um NAT. Teredo depende do uso de um servidor que pode ser publicamente e globalmente roteado para anunciarem conexões potenciais. O servidor Teredo fornece aplicativos cliente e servidor um ponto de reunião comum em que eles podem trocar informações de conexão. As máquinas, em seguida, solicitam um endereço de Teredo temporário e pacotes são encapsulados por meio da rede existente. Suporte a Teredo no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requer habilitar o suporte a IPv6 e Teredo no sistema operacional. [!INCLUDE[wxp](../../../../includes/wxp-md.md)]e suporte a sistemas operacionais posteriores Teredo. [!INCLUDE[wv](../../../../includes/wv-md.md)]e sistemas operacionais posteriores oferecem suporte ao IPv6 por padrão e requer apenas que o usuário habilitar Teredo. [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]e [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] requer que o usuário habilitar o IPv6 e Teredo. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]o [visão geral de Teredo](http://go.microsoft.com/fwlink/?LinkId=87571).  
  
## <a name="choosing-a-transport-and-message-exchange-pattern"></a>Escolhendo um transporte e padrões de troca de mensagem  
 Selecionando um transporte e MEPS é um processo de três etapas:  
  
1.  Analise o endereçamento de máquinas de ponto de extremidade. Servidores corporativos normalmente têm endereçamento direto, enquanto os usuários finais normalmente têm seu Endereçabilidade bloqueada pelo NAT. Se ambos os pontos de extremidade estiverem atrás de um NAT, como em cenários de ponto a ponto entre os usuários finais, em seguida, talvez seja necessário uma tecnologia, como o Teredo para fornecer capacidade de endereçamento.  
  
2.  Analise as restrições de protocolo e porta das máquinas de ponto de extremidade. Servidores corporativos normalmente estão atrás de firewalls de alta seguras que bloqueiam várias portas. No entanto, a porta 80 é frequentemente aberta para permitir o tráfego HTTP e a porta 443 está aberta para permitir o tráfego HTTPS. Os usuários finais são menos propensos a restrições de porta, mas pode ser protegido por um firewall que permita somente conexões de saída. Alguns firewalls permitem o gerenciamento por aplicativos no ponto de extremidade seletivamente abrir conexões.  
  
3.  Computação de transportes e MEPs que permite que as restrições de porta e capacidade de endereçamento da rede.  
  
 Uma topologia comuns para aplicativos cliente / servidor é que os clientes que estão atrás de um NAT sem Teredo com um firewall somente de saída e um servidor que está diretamente endereçável com um firewall de alta segurança. Neste cenário, o transporte TCP com um MEPS duplex e um transporte HTTP com uma solicitação-resposta MEPS funcionam bem. Uma topologia comuns para aplicativos de ponto a ponto é que ambos os pontos de extremidade por trás de NATs e firewalls. Nesse cenário e em cenários em que a topologia de rede é desconhecida, considere as seguintes recomendações:  
  
-   Não use transportes duplos. Um transporte duplo abre mais conexões, o que reduz a probabilidade de se conectar com êxito.  
  
-   Suporte a estabelecer canais de volta sobre a conexão de origem. Usando canais de volta, como em TCP duplex, abre menos conexões, o que aumenta a probabilidade de se conectar com êxito.  
  
-   Usar um serviço pode ser acessado para registrar pontos de extremidade ou retransmitir o tráfego. Usando um serviço de conexão global pode ser acessado, como um servidor Teredo, aumenta a probabilidade de se conectar com êxito quando a topologia de rede é restritiva ou desconhecido.  
  
 As tabelas a seguir examine o unidirecional, solicitação-resposta e MEPs duplex e o TCP padrão, TCP com Teredo e transportes HTTP padrão e duas em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
|Endereçamento|Direto de servidor|Servidor direto com NAT transversal|Servidor NAT|Servidor NAT com NAT transversal|  
|--------------------|-------------------|--------------------------------------|----------------|-----------------------------------|  
|Direto do cliente|Qualquer transporte e MEPS|Qualquer transporte e MEPS|Não há suporte.|Não há suporte.|  
|Cliente diretamente com o percurso de NAT|Qualquer transporte e MEPS.|Qualquer transporte e MEPS.|Não há suporte.|TCP com Teredo e qualquer MEPS. [!INCLUDE[wv](../../../../includes/wv-md.md)]tem uma opção de configuração de máquina para o suporte HTTP com Teredo.|  
|Cliente NAT|Qualquer transporte não dual e MEPS. Duplex MEPS requer o transporte TCP.|Qualquer transporte não dual e MEPS. Duplex MEPS requer o transporte TCP.|Não há suporte.|Não há suporte.|  
|Cliente NAT com NAT transversal|Qualquer transporte não dual e MEPS. Duplex MEPS requer o transporte TCP.|HTTP quase dupla e qualquer MEPS. Duplex MEPS requer o transporte TCP. Transporte TCP dupla requer Teredo. [!INCLUDE[wv](../../../../includes/wv-md.md)]tem uma opção de configuração de máquina para o suporte HTTP com Teredo.|Não há suporte.|TCP com Teredo e qualquer MEPS. [!INCLUDE[wv](../../../../includes/wv-md.md)]tem uma opção de configuração de máquina para o suporte HTTP com Teredo.|  
  
|Restrições de firewall|Servidor aberto|Servidor de firewall gerenciado|Servidor com o firewall somente HTTP|Servidor com o firewall apenas de saída|  
|---------------------------|-----------------|----------------------------------|-------------------------------------|-----------------------------------------|  
|Abrir do cliente|Qualquer transporte e MEPS.|Qualquer transporte e MEPS.|Qualquer transporte HTTP e MEPS.|Não há suporte.|  
|Cliente com o firewall gerenciado|Qualquer transporte não dual e MEPS. Duplex MEPS requer o transporte TCP.|Qualquer transporte não dual e MEPS. Duplex MEPS requer o transporte TCP.|Qualquer transporte HTTP e MEPS.|Não há suporte.|  
|Cliente com o firewall somente HTTP|Qualquer transporte HTTP e MEPS.|Qualquer transporte HTTP e MEPS.|Qualquer transporte HTTP e MEPS.|Não há suporte.|  
|Cliente com o firewall apenas de saída|Qualquer transporte não dual e MEPS. Duplex MEPS requer o transporte TCP.|Qualquer transporte não dual e MEPS. Duplex MEPS requer o transporte TCP.|Qualquer transporte HTTP e qualquer MEPS não-duplex.|Não há suporte.|
