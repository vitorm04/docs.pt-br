---
title: "Usando manipulações e inércia em um aplicativo XNA"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
caps.latest.revision: 7
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7d623a8c2276811ae443a4d745faffeeb79ffc6f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a><span data-ttu-id="b16aa-102">Usando manipulações e inércia em um aplicativo XNA</span><span class="sxs-lookup"><span data-stu-id="b16aa-102">Using Manipulations and Inertia in an XNA Application</span></span>
<span data-ttu-id="b16aa-103">Este artigo descreve como você pode usar manipulações e processamento de inércia em um aplicativo Microsoft XNA para controlar o movimento das partes do jogo.</span><span class="sxs-lookup"><span data-stu-id="b16aa-103">This article describes how you can use manipulations and inertia processing in a Microsoft XNA application to control the movement of game pieces.</span></span> <span data-ttu-id="b16aa-104">Antes de ler este artigo, você deve estar familiarizado com o tópico [Visão geral de manipulações e inércia](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) e com os conceitos de programação básicos de XNA.</span><span class="sxs-lookup"><span data-stu-id="b16aa-104">Before you read this article, you should be familiar with the [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) topic, and be familiar with basic XNA programming concepts.</span></span>  
  
 <span data-ttu-id="b16aa-105">Para executar as tarefas descritas neste artigo, seu projeto do XNA deve referenciar o assembly <xref:System.Windows.Input.Manipulations> e você deverá ter o [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([baixar](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) instalado em seu computador para que seu projeto possa referenciar os assemblies do XNA.</span><span class="sxs-lookup"><span data-stu-id="b16aa-105">To perform the tasks described in this article, your XNA project must reference the <xref:System.Windows.Input.Manipulations> assembly, and you must have [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([download](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) installed on your computer so that your project can reference the XNA assemblies.</span></span>  
  
## <a name="overview-of-functionality"></a><span data-ttu-id="b16aa-106">Visão geral da funcionalidade</span><span class="sxs-lookup"><span data-stu-id="b16aa-106">Overview of Functionality</span></span>  
 <span data-ttu-id="b16aa-107">Este artigo mostra como criar uma classe personalizada que representa uma parte do jogo que use manipulação e processamento de inércia.</span><span class="sxs-lookup"><span data-stu-id="b16aa-107">This article shows you how to create a custom class that represents a game piece that uses manipulation and inertia processing.</span></span> <span data-ttu-id="b16aa-108">Essa classe permite que você manipule uma parte do jogo pela tela arrastando-a com o mouse e, em seguida, liberando-a.</span><span class="sxs-lookup"><span data-stu-id="b16aa-108">This class enables you to manipulate a game piece across the screen by dragging it with the mouse, and then releasing it.</span></span> <span data-ttu-id="b16aa-109">Uma vez liberada, o processamento de inércia mantém a parte do jogo se movendo lentamente até parar.</span><span class="sxs-lookup"><span data-stu-id="b16aa-109">Once released, inertia processing keeps the game piece moving as it gradually slows down.</span></span> <span data-ttu-id="b16aa-110">O movimento é linear e angular.</span><span class="sxs-lookup"><span data-stu-id="b16aa-110">Movement is both linear and angular.</span></span>  
  
 <span data-ttu-id="b16aa-111">![Um aplicativo simples de manipulações e inércia. ](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span><span class="sxs-lookup"><span data-stu-id="b16aa-111">![A simple manipulations and inertia application.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span></span>  
  
 <span data-ttu-id="b16aa-112">Além disso, é criada uma coleção personalizada que gerencia várias partes do jogo.</span><span class="sxs-lookup"><span data-stu-id="b16aa-112">In addition, a custom collection is created that manages multiple game pieces.</span></span> <span data-ttu-id="b16aa-113">Isso simplifica a manipulação necessária da classe XNA Game.</span><span class="sxs-lookup"><span data-stu-id="b16aa-113">This simplifies the handling that is required from the XNA Game class.</span></span>  
  
 [<span data-ttu-id="b16aa-114">Criação da classe GamePiece</span><span class="sxs-lookup"><span data-stu-id="b16aa-114">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [<span data-ttu-id="b16aa-115">Criação da classe GamePieceCollection</span><span class="sxs-lookup"><span data-stu-id="b16aa-115">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [<span data-ttu-id="b16aa-116">Criação da classe Game1</span><span class="sxs-lookup"><span data-stu-id="b16aa-116">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [<span data-ttu-id="b16aa-117">Listagens de códigos completas</span><span class="sxs-lookup"><span data-stu-id="b16aa-117">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a><span data-ttu-id="b16aa-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b16aa-118">See Also</span></span>  
 <span data-ttu-id="b16aa-119"><xref:System.Windows.Input.Manipulations></span><span class="sxs-lookup"><span data-stu-id="b16aa-119"><xref:System.Windows.Input.Manipulations></span></span>   
 [<span data-ttu-id="b16aa-120">Visão geral de manipulações e inércia</span><span class="sxs-lookup"><span data-stu-id="b16aa-120">Manipulations and Inertia Overview</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)

