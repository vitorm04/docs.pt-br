---
title: Como criar uma coleção usada por um inicializador de coleção
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: b332ffb44ebc20ce8431e586fc380b8c6a29967d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086368"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="31ba8-102">Como criar uma coleção usada por um inicializador de coleção (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31ba8-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>

<span data-ttu-id="31ba8-103">Quando você usa um inicializador de coleção para criar uma coleção, o compilador Visual Basic procura um `Add` método do tipo de coleção para o qual os parâmetros do `Add` método correspondem aos tipos de valores no inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="31ba8-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="31ba8-104">Esse `Add` método é usado para popular a coleção com os valores do inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="31ba8-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31ba8-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="31ba8-105">Example</span></span>  

 <span data-ttu-id="31ba8-106">O exemplo a seguir mostra uma `OrderCollection` coleção que contém um `Add` método público que um inicializador de coleção pode usar para adicionar objetos do tipo `Order` .</span><span class="sxs-lookup"><span data-stu-id="31ba8-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="31ba8-107">O `Add` método permite que você use a sintaxe de inicializador de coleção abreviada.</span><span class="sxs-lookup"><span data-stu-id="31ba8-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="31ba8-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="31ba8-108">See also</span></span>

- [<span data-ttu-id="31ba8-109">Inicializadores de coleção</span><span class="sxs-lookup"><span data-stu-id="31ba8-109">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="31ba8-110">Como criar um método para adicionar extensão usado por um inicializador de coleção</span><span class="sxs-lookup"><span data-stu-id="31ba8-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
