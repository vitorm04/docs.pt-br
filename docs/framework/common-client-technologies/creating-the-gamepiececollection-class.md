---
title: Criando a classe GamePieceCollection
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b74702d71113c3a9dac654971e7d02f97016218b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="creating-the-gamepiececollection-class"></a><span data-ttu-id="5970e-102">Criando a classe GamePieceCollection</span><span class="sxs-lookup"><span data-stu-id="5970e-102">Creating the GamePieceCollection Class</span></span>
<span data-ttu-id="5970e-103">A classe **GamePieceCollection** deriva da classe List genérica e introduz métodos para gerenciar com mais facilidade vários objetos **GamePiece**.</span><span class="sxs-lookup"><span data-stu-id="5970e-103">The **GamePieceCollection** class derives from the generic List class, and introduces methods to more easily manage multiple **GamePiece** objects.</span></span>  
  
## <a name="creating-the-code"></a><span data-ttu-id="5970e-104">Criando o código</span><span class="sxs-lookup"><span data-stu-id="5970e-104">Creating the Code</span></span>  
 <span data-ttu-id="5970e-105">O construtor da classe **GamePieceCollection** inicializa o membro particular *capturedIndex*.</span><span class="sxs-lookup"><span data-stu-id="5970e-105">The constructor of the **GamePieceCollection** class initializes the private member *capturedIndex*.</span></span> <span data-ttu-id="5970e-106">Esse campo é usado para controlar qual das peças do jogo tem a captura do mouse no momento.</span><span class="sxs-lookup"><span data-stu-id="5970e-106">This field is used to track which of the game pieces currently has the mouse capture.</span></span>  
  
 <span data-ttu-id="5970e-107">[!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]</span><span class="sxs-lookup"><span data-stu-id="5970e-107">[!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]</span></span>  
  
 <span data-ttu-id="5970e-108">Os métodos **ProcessInertia** e **Draw** simplificam o código necessário nos métodos [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) e [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) do jogo enumerando todas as peças do jogo na coleção e chamando o respectivo método em cada objeto **GamePiece**.</span><span class="sxs-lookup"><span data-stu-id="5970e-108">The **ProcessInertia** and the **Draw** methods simplify the code needed in the game [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) and [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) methods by enumerating all of the game pieces in the collection and calling the respective method on each **GamePiece** object.</span></span>  
  
 <span data-ttu-id="5970e-109">[!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]</span><span class="sxs-lookup"><span data-stu-id="5970e-109">[!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]</span></span>  
  
 <span data-ttu-id="5970e-110">O método **UpdateFromMouse** também é chamado durante a atualização do jogo.</span><span class="sxs-lookup"><span data-stu-id="5970e-110">The **UpdateFromMouse** method is also called during game update.</span></span> <span data-ttu-id="5970e-111">Ele permite que somente uma peça do jogo tenha a captura do mouse verificando primeiro se a captura atual (se houver) ainda está em vigor.</span><span class="sxs-lookup"><span data-stu-id="5970e-111">It enables only one game piece to have the mouse capture by first checking to see if the current capture (if any) is still in effect.</span></span> <span data-ttu-id="5970e-112">Nesse caso, nenhuma outra peça tem permissão para verificar a captura.</span><span class="sxs-lookup"><span data-stu-id="5970e-112">If so, no other piece is allowed to check for capture.</span></span>  
  
 <span data-ttu-id="5970e-113">Se nenhuma peça tiver a captura no momento, o método **UpdateFromMouse** enumera cada peça do jogo da última para a primeira e verifica se essa peça relata uma captura do mouse.</span><span class="sxs-lookup"><span data-stu-id="5970e-113">If no piece currently has the capture, the **UpdateFromMouse** method enumerates each game piece from last to first, and checks to see if that piece reports a mouse capture.</span></span> <span data-ttu-id="5970e-114">Nesse caso, essa peça se torna a peça atualmente capturada e não ocorre nenhum processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="5970e-114">If so, that piece becomes the current captured piece, and no further processing takes place.</span></span> <span data-ttu-id="5970e-115">O método **UpdateFromMouse** verifica o último item na coleção primeiro para que se houver duas peças sobrepostas, a com a ordem de Z maior obtenha a captura.</span><span class="sxs-lookup"><span data-stu-id="5970e-115">The **UpdateFromMouse** method checks the last item in the collection first so that if two pieces are overlapped, the one with the higher Z-order will obtain the capture.</span></span> <span data-ttu-id="5970e-116">A ordem Z não é explícita ou alterável, ela é controlada simplesmente pela ordem em que as peças do jogo são adicionadas à coleção.</span><span class="sxs-lookup"><span data-stu-id="5970e-116">Z-order is not explicit nor changeable; it is governed simply by the order in which game pieces are added to the collection.</span></span>  
  
 <span data-ttu-id="5970e-117">[!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]</span><span class="sxs-lookup"><span data-stu-id="5970e-117">[!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5970e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5970e-118">See Also</span></span>  
 <span data-ttu-id="5970e-119">[Manipulações e inércia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md) </span><span class="sxs-lookup"><span data-stu-id="5970e-119">[Manipulations and Inertia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md) </span></span>  
 <span data-ttu-id="5970e-120">[Usando manipulações e inércia em um aplicativo XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md) </span><span class="sxs-lookup"><span data-stu-id="5970e-120">[Using Manipulations and Inertia in an XNA Application](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md) </span></span>  
 <span data-ttu-id="5970e-121">[Criando a classe GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md) </span><span class="sxs-lookup"><span data-stu-id="5970e-121">[Creating the GamePiece Class](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md) </span></span>  
 <span data-ttu-id="5970e-122">[Criação da classe Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md) </span><span class="sxs-lookup"><span data-stu-id="5970e-122">[Creating the Game1 Class](../../../docs/framework/common-client-technologies/creating-the-game1-class.md) </span></span>  
 [<span data-ttu-id="5970e-123">Listagens de códigos completas</span><span class="sxs-lookup"><span data-stu-id="5970e-123">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)

