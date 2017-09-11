---
title: Criando a classe Game1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
caps.latest.revision: 8
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9c6d0bdfd21f431ae6da38e3868386f91d5b725b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="creating-the-game1-class"></a><span data-ttu-id="9425c-102">Criando a classe Game1</span><span class="sxs-lookup"><span data-stu-id="9425c-102">Creating the Game1 Class</span></span>
<span data-ttu-id="9425c-103">Como com todos os projetos de Microsoft XNA, a classe Game1 é derivada da classe [Microsoft.Xna.Framework.Game](http://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx), que fornece a inicialização do dispositivo de gráficos básicos, lógica de jogo e processamento de código para jogos XNA.</span><span class="sxs-lookup"><span data-stu-id="9425c-103">As with all Microsoft XNA projects, the Game1 class derives from the [Microsoft.Xna.Framework.Game](http://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) class, which provides basic graphics device initialization, game logic, and rendering code for XNA games.</span></span> <span data-ttu-id="9425c-104">A classe Game1 é bastante simples, pois a maioria do trabalho é realizado nas classes GamePiece e GamePieceCollection.</span><span class="sxs-lookup"><span data-stu-id="9425c-104">The Game1 class is fairly simple because most of the work in done in the GamePiece and GamePieceCollection classes.</span></span>  
  
## <a name="creating-the-code"></a><span data-ttu-id="9425c-105">Criando o código</span><span class="sxs-lookup"><span data-stu-id="9425c-105">Creating the Code</span></span>  
 <span data-ttu-id="9425c-106">Os membros particulares da classe consistem em um objeto **GamePieceCollection** para conter as partes do jogo, um objeto [GraphicsDeviceManager](http://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) e um objeto [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) usado para renderizar as partes do jogo.</span><span class="sxs-lookup"><span data-stu-id="9425c-106">The private members for the class consist of a **GamePieceCollection** object to hold the game pieces, a [GraphicsDeviceManager](http://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) object, and a [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) object used to render game pieces.</span></span>  
  
 <span data-ttu-id="9425c-107">[!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]</span><span class="sxs-lookup"><span data-stu-id="9425c-107">[!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]</span></span>  
  
 <span data-ttu-id="9425c-108">Durante a inicialização do jogo, esses objetos são instanciados.</span><span class="sxs-lookup"><span data-stu-id="9425c-108">During game initialization, these objects are instantiated.</span></span>  
  
 <span data-ttu-id="9425c-109">[!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]</span><span class="sxs-lookup"><span data-stu-id="9425c-109">[!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]</span></span>  
  
 <span data-ttu-id="9425c-110">Quando o método [LoadContent](http://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) é chamado, as partes do jogo são criadas e atribuídas ao objeto **GamePieceCollection**.</span><span class="sxs-lookup"><span data-stu-id="9425c-110">When the [LoadContent](http://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) method is called, the game pieces are created and assigned to the **GamePieceCollection** object.</span></span> <span data-ttu-id="9425c-111">Existem dois tipos de partes do jogo.</span><span class="sxs-lookup"><span data-stu-id="9425c-111">There are two types of game pieces.</span></span> <span data-ttu-id="9425c-112">A escala das partes é ligeiramente alterada para permitir partes menores e maiores.</span><span class="sxs-lookup"><span data-stu-id="9425c-112">The scale factor for the pieces is changed slightly so that there are some smaller and some larger pieces.</span></span>  
  
 <span data-ttu-id="9425c-113">[!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]</span><span class="sxs-lookup"><span data-stu-id="9425c-113">[!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]</span></span>  
  
 <span data-ttu-id="9425c-114">O método [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) é chamado repetidamente com o XNA Framework durante a execução do jogo.</span><span class="sxs-lookup"><span data-stu-id="9425c-114">The [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) method is called repeatedly by the XNA Framework while the game is running.</span></span> <span data-ttu-id="9425c-115">O método [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) chama os métodos **ProcessInertia** e **UpdateFromMouse** na coleção de partes do jogo.</span><span class="sxs-lookup"><span data-stu-id="9425c-115">The [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) method calls the **ProcessInertia** and the **UpdateFromMouse** methods on the game piece collection.</span></span> <span data-ttu-id="9425c-116">Esses métodos são descritos em [Criando a classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).</span><span class="sxs-lookup"><span data-stu-id="9425c-116">These methods are described in [Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).</span></span>  
  
 <span data-ttu-id="9425c-117">[!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]</span><span class="sxs-lookup"><span data-stu-id="9425c-117">[!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]</span></span>  
  
 <span data-ttu-id="9425c-118">O método [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) também é chamado repetidamente pelo XNA Framework durante a execução do jogo.</span><span class="sxs-lookup"><span data-stu-id="9425c-118">The [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) method is also called repeatedly by the XNA Framework while the game is running.</span></span> <span data-ttu-id="9425c-119">O método [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) realiza a renderização das partes do jogo chamando o método **Draw** do objeto **GamePieceCollection**.</span><span class="sxs-lookup"><span data-stu-id="9425c-119">The [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) method performs the rendering of game pieces by calling the **Draw** method of the **GamePieceCollection** object.</span></span> <span data-ttu-id="9425c-120">Esses método é descrito em [Criando a classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).</span><span class="sxs-lookup"><span data-stu-id="9425c-120">This method is described in[Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).</span></span>  
  
 <span data-ttu-id="9425c-121">[!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]</span><span class="sxs-lookup"><span data-stu-id="9425c-121">[!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9425c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9425c-122">See Also</span></span>  
 <span data-ttu-id="9425c-123">[Manipulações e inércia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md) </span><span class="sxs-lookup"><span data-stu-id="9425c-123">[Manipulations and Inertia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md) </span></span>  
 <span data-ttu-id="9425c-124">[Usando manipulações e inércia em um aplicativo XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md) </span><span class="sxs-lookup"><span data-stu-id="9425c-124">[Using Manipulations and Inertia in an XNA Application](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md) </span></span>  
 <span data-ttu-id="9425c-125">[Criando a classe GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md) </span><span class="sxs-lookup"><span data-stu-id="9425c-125">[Creating the GamePiece Class](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md) </span></span>  
 <span data-ttu-id="9425c-126">[Criando a classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) </span><span class="sxs-lookup"><span data-stu-id="9425c-126">[Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) </span></span>  
 [<span data-ttu-id="9425c-127">Listagens de códigos completas</span><span class="sxs-lookup"><span data-stu-id="9425c-127">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)

