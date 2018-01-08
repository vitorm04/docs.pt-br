---
title: "Usando manipulações e inércia em um aplicativo XNA"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7452a6001742bc9e0456ccb6339f13596a2ab72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a>Usando manipulações e inércia em um aplicativo XNA
Este artigo descreve como você pode usar manipulações e processamento de inércia em um aplicativo Microsoft XNA para controlar o movimento das partes do jogo. Antes de ler este artigo, você deve estar familiarizado com o tópico [Visão geral de manipulações e inércia](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) e com os conceitos de programação básicos de XNA.  
  
 Para executar as tarefas descritas neste artigo, seu projeto do XNA deve referenciar o assembly <xref:System.Windows.Input.Manipulations> e você deverá ter o [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([baixar](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) instalado em seu computador para que seu projeto possa referenciar os assemblies do XNA.  
  
## <a name="overview-of-functionality"></a>Visão geral da funcionalidade  
 Este artigo mostra como criar uma classe personalizada que representa uma parte do jogo que use manipulação e processamento de inércia. Essa classe permite que você manipule uma parte do jogo pela tela arrastando-a com o mouse e, em seguida, liberando-a. Uma vez liberada, o processamento de inércia mantém a parte do jogo se movendo lentamente até parar. O movimento é linear e angular.  
  
 ![Um aplicativo simples de manipulações e inércia. ](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")  
  
 Além disso, é criada uma coleção personalizada que gerencia várias partes do jogo. Isso simplifica a manipulação necessária da classe XNA Game.  
  
 [Criação da classe GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [Criação da classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [Criação da classe Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [Listagens de códigos completas](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Input.Manipulations>  
 [Visão geral de manipulações e inércia](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
