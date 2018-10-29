---
title: Visão geral de manipulações e inércia
ms.date: 03/30/2017
ms.assetid: dd31b89b-eab6-45a1-8d0b-11e0eb84b234
ms.openlocfilehash: 6396c174b341b5ae937fa931488ee1bd3a5fcbd5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187813"
---
# <a name="manipulations-and-inertia-overview"></a>Visão geral de manipulações e inércia
As *manipulações* permitem aos usuários mover, girar e redimensionar elementos de interface do usuário usando *manipuladores*. Um manipulador representa um mouse ou (em um cenário sensível ao toque) uma caneta ou um dedo.  
  
 A *inércia* emula o comportamento do mundo real para elementos de interface do usuário que estão em movimento simulando forças de atrito nos elementos. Isso permite que elementos reduzam gradualmente a movimentação (linear e angular) antes de uma parada. Este artigo fornece uma introdução às manipulações e à inércia para o .NET Framework.  
  
## <a name="manipulations"></a>Manipulações  
 Uma manipulação trata uma coleção de manipuladores como um objeto de composição. Um aplicativo pode rastrear as alterações para o objeto de composição, em vez de componentes individuais.  
  
 Considere a imagem na ilustração a seguir. Um usuário pode usar dois manipuladores para mover, girar e ajustar escala da imagem. As alterações para cada manipulador são interpretadas junto com os outros manipuladores.  
  
 Por exemplo, se você tiver dois manipuladores (1 e 2) na imagem e mover o manipulador 1 em uma direção +Y (para baixo), a alteração da imagem dependerá do que acontece com o manipulador 2. Se o manipulador 2 também move na direção +Y (para baixo), a imagem simplesmente se moverá na direção +Y. Mas se o manipulador 2 não mudar ou se mover em uma direção -Y (para cima), a imagem será reduzida ou girada.  
  
 ![Uma foto virtual que dois dedos estão manipulando. ](../../../docs/framework/common-client-technologies/media/manipulation-resize.png "Manipulation_Resize")  
  
 Uma imagem sendo manipulada por dois manipuladores  
  
 O processamento de manipulação fornece uma estrutura que monitora um subconjunto dos manipuladores e os interpreta como estivessem agindo em conjunto, em vez de independentemente. Você pode criar vários objetos de processador de manipulação ao mesmo tempo, um para cada elemento da interface do usuário a ser manipulado em um aplicativo. Um processador de manipulação é informado de quais dispositivos de entrada observar e ele relata as manipulações por meio de [eventos .NET](../../../docs/standard/events/index.md).  
  
 Um processador de manipulação não tem informações sobre o elemento específico que está sendo manipulado. Um aplicativo separadamente aplica as alterações a um elemento específico do aplicativo. Por exemplo, um aplicativo aplica transformações a uma imagem ou a redesenha para exibi-la em seu novo local ou com um novo tamanho ou orientação.  
  
 As manipulações são projetadas para [transformações afins](/windows/desktop/gdiplus/-gdiplus-transformations-use) bidimensionais (2D). Essas transformações incluem mover, girar e ajustar escala.  
  
### <a name="parts-of-a-manipulation"></a>Partes de uma manipulação  
 Uma manipulação é uma coleção de objetos <xref:System.Windows.Input.Manipulations.Manipulator2D>. Essa manipulação agregada é representada por um ponto de origem e uma elipse. O ponto de origem é a posição média de todos os manipuladores que estão manipulando um elemento. A elipse tem um raio que é a distância média da origem até cada um dos objetos <xref:System.Windows.Input.Manipulations.Manipulator2D>.  
  
 ![As partes de uma manipulação.](../../../docs/framework/common-client-technologies/media/manipulation-definition.png "Manipulation_Definition")  
  
 Dois manipuladores (1 e 2), uma origem e uma elipse especificam uma manipulação  
  
 Conforme os manipuladores são adicionados, movidos ou removidos de um elemento de interface do usuário, um aplicativo atualiza o objeto <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> chamando o método <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A>. Quando a manipulação começa pela primeira vez, o evento <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> é gerado.  
  
> [!NOTE]
> O processamento de manipulação é mais eficiente quando usado em um ambiente de atualização baseado em quadro. Ao usar o processamento de manipulação em um aplicativo Microsoft XNA, essa não é uma preocupação, pois a estrutura do XNA fornece atualizações baseadas em quadro usando o método [Game.Update](https://docs.microsoft.com/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29). Em outro ambiente (como WinForms), talvez seja necessário fornecer sua própria lógica baseada em quadro para coletar manipulações e enviá-los periodicamente para o método <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> como um lote.  
  
 Conforme o número de manipuladores ou sua posição muda, o evento <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> é gerado. As propriedades do objeto <xref:System.Windows.Input.Manipulations.Manipulation2DDeltaEventArgs> passado para o manipulador de eventos <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> especificam alterações na origem, escala, rotação e translação que ocorreram desde o último evento. A origem da manipulação muda quando os manipuladores se movem e quando os manipuladores são adicionados ou removidos. Os valores de translação especificam quanta movimentação de X ou Y a manipulação inclui.  
  
 Usando os novos valores, um aplicativo redesenha o elemento da interface do usuário.  
  
 ![Uma manipulação após o contato se mover para a direita.](../../../docs/framework/common-client-technologies/media/manipulation-changed.png "Manipulation_Changed")  
  
 O manipulador 1 se move e faz com que a origem mude  
  
 Quando o último manipulador associado à manipulação é removido do objeto <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D>, o evento <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> é gerado.  
  
### <a name="the-manipulation-processing-model"></a>O Modelo de Processamento de Manipulação  
 Um processador de manipulação usa um modelo de uso direto. Com esse modelo simples, um aplicativo deve passar todos os detalhes de eventos de entrada para o processador de manipulação. Um evento de entrada pode ser gerado por qualquer entrada primitiva, como um dispositivo de mouse, uma caneta ou um dedo. Esse processo fornece um mecanismo de filtragem direto e um modelo de uso simples, para que o aplicativo possa criar eventos de entrada em lote quando necessário.  
  
 Para um aplicativo incluir uma entrada primitiva no processo de manipulação, ele cria uma estrutura <xref:System.Windows.Input.Manipulations.Manipulator2D> dos detalhes da entrada primitiva e passa a estrutura para o processador de manipulação usando o método <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A>. O processador de manipulação, em seguida, gera eventos que o aplicativo deve tratar para atualizar o componente visual de maneira apropriada.  
  
 ![O fluxo do modelo de uso direto das manipulações.](../../../docs/framework/common-client-technologies/media/manipulation-flow.png "Manipulation_Flow")  
  
 O modelo de processamento de manipulação  
  
## <a name="inertia"></a>Inércia  
 O processador de inércia permite que aplicativos extrapolem o local, a orientação e outras propriedades de um elemento de interface do usuário simulando o comportamento do mundo real.  
  
 Por exemplo, quando um usuário movimenta um elemento, ele continua a se mover, desacelerar e, então, parar lentamente. O processador de inércia implementa esse comportamento fazendo com que os valores de 2D afins (origem, escala, translação e rotação) mudem ao longo do tempo especificado em uma taxa de desaceleração especificada.  
  
 Como com o processamento de manipulação, um processador de inércia não tem informações sobre um determinado elemento de interface do usuário. Em resposta a eventos que são gerados em um objeto <xref:System.Windows.Input.Manipulations.InertiaProcessor2D>, um aplicativo separadamente aplica as alterações a um elemento específico do aplicativo.  
  
 O processamento de inércia e o processamento de manipulação geralmente são usados juntos. Suas interfaces são semelhantes e os eventos que eles geram são (em alguns casos) idênticos. Em geral, o processamento de inércia começa quando a manipulação do elemento de interface do usuário é concluída. Isso é feito ouvindo o <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> evento e iniciando o processamento de inércia o manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Input.Manipulations>
