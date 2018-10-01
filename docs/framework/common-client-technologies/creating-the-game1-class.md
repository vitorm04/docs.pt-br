---
title: Criando a classe Game1
ms.date: 03/30/2017
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
ms.openlocfilehash: 368da9df4dffc7017abb02888bc2eb2641f04b8b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47201017"
---
# <a name="creating-the-game1-class"></a>Criando a classe Game1
Como com todos os projetos de Microsoft XNA, a classe Game1 é derivada da classe [Microsoft.Xna.Framework.Game](https://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx), que fornece a inicialização do dispositivo de gráficos básicos, lógica de jogo e processamento de código para jogos XNA. A classe Game1 é bastante simples, pois a maioria do trabalho é realizado nas classes GamePiece e GamePieceCollection.  
  
## <a name="creating-the-code"></a>Criando o código  
 Os membros particulares da classe consistem em um objeto **GamePieceCollection** para conter as partes do jogo, um objeto [GraphicsDeviceManager](https://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) e um objeto [SpriteBatch](https://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) usado para renderizar as partes do jogo.  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 Durante a inicialização do jogo, esses objetos são instanciados.  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 Quando o método [LoadContent](https://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) é chamado, as partes do jogo são criadas e atribuídas ao objeto **GamePieceCollection**. Existem dois tipos de partes do jogo. A escala das partes é ligeiramente alterada para permitir partes menores e maiores.  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 O método [Update](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) é chamado repetidamente com o XNA Framework durante a execução do jogo. O método [Update](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) chama os métodos **ProcessInertia** e **UpdateFromMouse** na coleção de partes do jogo. Esses métodos são descritos em [Criando a classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 O método [Draw](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) também é chamado repetidamente pelo XNA Framework durante a execução do jogo. O método [Draw](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) realiza a renderização das partes do jogo chamando o método **Draw** do objeto **GamePieceCollection**. Esses método é descrito em [Criando a classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a>Consulte também  
 [Manipulações e inércia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Uso de manipulações e inércia em um aplicativo XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Criação da classe GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Criação da classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Listagens de códigos completas](../../../docs/framework/common-client-technologies/full-code-listings.md)
