---
title: Planejando-se para desempenho do aplicativo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6bdb140d90de02fa817c55a05f40e57fcd0d636c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="planning-for-application-performance"></a>Planejando-se para desempenho do aplicativo
O sucesso de alcançar suas metas de desempenho depende de quão bem você desenvolve sua estratégia de desempenho. O planejamento é o primeiro estágio no desenvolvimento de qualquer produto. Este tópico descreve algumas regras bastante simples para desenvolver uma boa estratégia de desempenho.  
  
## <a name="think-in-terms-of-scenarios"></a>Pense em termos de cenários  
 Cenários podem ajudá-lo a focar nos componentes importantes do seu aplicativo. Cenários geralmente são derivados de clientes, bem como de produtos da concorrência. Sempre estude seus clientes e descubra o que realmente os empolga quanto ao seu produto e aos produtos dos seus concorrentes. Os comentários dos clientes podem ajudá-lo a determinar o principal cenário do aplicativo. Por exemplo, se você estiver criando um componente que será usado durante a inicialização, será provável que o componente seja chamado somente uma vez, quando o aplicativo for inicializado. O tempo de inicialização torna-se seu cenário principal. Outros exemplos de cenários-chave podem ser a taxa de quadros desejada para sequências de animação ou o conjunto máximo de trabalho permitido para o aplicativo.  
  
## <a name="define-goals"></a>Definir metas  
 Metas ajudam a determinar se o desempenho de um aplicativo está mais rápido ou mais lento. Você deve definir metas para todos os seus cenários. Todas as metas de desempenho que você definir devem se basear nas expectativas de seus clientes. Pode ser difícil definir metas de desempenho no início do ciclo de desenvolvimento de aplicativos, quando há ainda muitos problemas não resolvidos. No entanto, é melhor definir uma meta inicial e revisá-la mais tarde do que não ter meta alguma.  
  
## <a name="understand-your-platform"></a>Compreenda sua plataforma  
 Sempre mantenha o ciclo de medir, investigar, refinar/corrigir durante seu ciclo de desenvolvimento de aplicativos. Do início até o fim do ciclo de desenvolvimento, você precisa avaliar o desempenho do seu aplicativo em um ambiente confiável e estável. Você deve evitar variabilidade causada por fatores externos. Por exemplo, ao testar o desempenho, desabilite programas antivírus ou qualquer atualização automática, como o SMS, para que não afetem os resultados de teste de desempenho. Depois de ter medido o desempenho do aplicativo, é preciso identificar as alterações que resultarão nos maiores aperfeiçoamentos. Depois de modificar seu aplicativo, inicie o ciclo novamente.  
  
## <a name="make-performance-tuning-an-iterative-process"></a>Tornar o ajuste de desempenho um processo iterativo  
 Você deve saber o custo relativo de cada recurso que usará. Por exemplo, a reflexão em [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] geralmente faz uso intenso de desempenho em termos de recursos de computação, portanto use-o criteriosamente. Isso não significa evitar o uso da reflexão, apenas que você deve ter cuidado para equilibrar os requisitos de desempenho do aplicativo com as demandas de desempenho dos recursos que você usa.  
  
## <a name="build-towards-graphical-richness"></a>Compilando com foco em riqueza gráfica  
 Uma técnica-chave para criar uma abordagem escalonável para atingir desempenho do aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é criar pensando em riqueza e complexidade gráficas. Sempre comece usando os recursos com uso menos intenso de desempenho para atingir suas metas de cenário. Depois que você atingir essas metas, compile para obter riqueza gráfica usando recursos com uso mais intenso de desempenho, sempre mantendo suas metas de cenário em mente. Lembre-se de que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é uma plataforma muito sofisticada e oferece recursos gráficos muito ricos. Utilizar recursos com uso intenso de desempenho sem pensar pode afetar negativamente o desempenho geral do aplicativo.  
  
 Controles do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são inerentemente extensíveis permitindo ampla personalização de sua aparência sem alterar o comportamento do controle. Ao aproveitar estilos, modelos de dados e modelos de controle, você pode criar e incrementalmente aprimorar um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] personalizável que se adapta às suas necessidades de desempenho.  
  
## <a name="see-also"></a>Consulte também  
 [Otimizando o desempenho do aplicativo WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Aproveitando o hardware](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Layout e design](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Elementos gráficos e geração de imagens 2D](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Comportamento do objeto](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Recursos do aplicativo](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Texto](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Associação de dados](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Outras recomendações de desempenho](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
