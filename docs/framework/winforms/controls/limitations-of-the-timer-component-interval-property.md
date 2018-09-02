---
title: Limitações da propriedade de intervalo do componente de temporizador dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: e5b9e7e43369913f0cdc9c7f2111bd4fe58675e6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465649"
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a>Limitações da propriedade de intervalo do componente de temporizador dos Windows Forms
Os formulários do Windows <xref:System.Windows.Forms.Timer> componente tem um <xref:System.Windows.Forms.Timer.Interval%2A> propriedade que especifica o número de milissegundos que passam entre um evento de temporizador e o próximo. A menos que o componente está desativado, um temporizador continua recebendo o <xref:System.Windows.Forms.Timer.Tick> evento em intervalos aproximadamente iguais de tempo.  
  
 Esse componente foi projetado para um ambiente do Windows Forms. Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
## <a name="the-interval-property"></a>A propriedade Interval  
 O <xref:System.Windows.Forms.Timer.Interval%2A> propriedade tem algumas limitações a serem consideradas quando você está programando um <xref:System.Windows.Forms.Timer> componente:  
  
-   Se seu aplicativo ou outro aplicativo estiver criando grandes demandas no sistema — como loops longos, cálculos intensivos, unidade, rede ou acesso à porta — seu aplicativo poderá não receber eventos com a frequência do temporizador como o <xref:System.Windows.Forms.Timer.Interval%2A> propriedade especifica.  
  
-   Não há garantia de que o intervalo decorra exatamente na hora. Para garantir a precisão, o temporizador deve verificar o relógio do sistema conforme necessário, em vez de tentar manter o controle de tempo acumulado internamente.  
  
-   A precisão do <xref:System.Windows.Forms.Timer.Interval%2A> propriedade é em milissegundos. Alguns computadores fornecem um contador de alta resolução que tem uma resolução maior do que milissegundos. A disponibilidade desse contador depende do hardware do processador do computador. Para obter mais informações, consulte o artigo 172338, "Como para usar QueryPerformanceCounter para código de tempo" na Base de dados de Conhecimento Microsoft em http://support.microsoft.com.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Timer>  
 [Componente Timer](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Visão geral do componente de temporizador](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
