---
title: Criando a classe GamePieceCollection | Microsoft Docs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4b037ee-1201-4a55-b198-0d6532ed6f35
caps.latest.revision: 8
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 672d2717905195084c381ea692aa426b5e3ca09c
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="creating-the-gamepiececollection-class"></a>Criando a classe GamePieceCollection
A classe **GamePieceCollection** deriva da classe List genérica e introduz métodos para gerenciar com mais facilidade vários objetos **GamePiece**.  
  
## <a name="creating-the-code"></a>Criando o código  
 O construtor da classe **GamePieceCollection** inicializa o membro particular *capturedIndex*. Esse campo é usado para controlar qual das peças do jogo tem a captura do mouse no momento.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]  
  
 Os métodos **ProcessInertia** e **Draw** simplificam o código necessário nos métodos [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) e [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) do jogo enumerando todas as peças do jogo na coleção e chamando o respectivo método em cada objeto **GamePiece**.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]  
  
 O método **UpdateFromMouse** também é chamado durante a atualização do jogo. Ele permite que somente uma peça do jogo tenha a captura do mouse verificando primeiro se a captura atual (se houver) ainda está em vigor. Nesse caso, nenhuma outra peça tem permissão para verificar a captura.  
  
 Se nenhuma peça tiver a captura no momento, o método **UpdateFromMouse** enumera cada peça do jogo da última para a primeira e verifica se essa peça relata uma captura do mouse. Nesse caso, essa peça se torna a peça atualmente capturada e não ocorre nenhum processamento adicional. O método **UpdateFromMouse** verifica o último item na coleção primeiro para que se houver duas peças sobrepostas, a com a ordem de Z maior obtenha a captura. A ordem Z não é explícita ou alterável, ela é controlada simplesmente pela ordem em que as peças do jogo são adicionadas à coleção.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]  
  
## <a name="see-also"></a>Consulte também  
 [Manipulações e inércia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)   
 [Usando manipulações e inércia em um aplicativo XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)   
 [Criando a classe GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)   
 [Criação da classe Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)   
 [Listagens de códigos completas](../../../docs/framework/common-client-technologies/full-code-listings.md)
