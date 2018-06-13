---
title: Como criar uma coleção usada por um inicializador de coleção (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 6158b6f02d95260e2955e77d732fae8b8d9d5e04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654155"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="bf152-102">Como criar uma coleção usada por um inicializador de coleção (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf152-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="bf152-103">Quando você usa um inicializador de coleção para criar uma coleção, o compilador do Visual Basic procura um `Add` método do tipo de coleção para a qual os parâmetros para o `Add` método correspondem aos tipos de valores em um inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="bf152-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="bf152-104">Isso `Add` método é usado para preencher a coleção com os valores do inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="bf152-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf152-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bf152-105">Example</span></span>  
 <span data-ttu-id="bf152-106">A exemplo a seguir mostra um `OrderCollection` coleção que contém um público `Add` método utilizado um inicializador de coleção para adicionar objetos do tipo `Order`.</span><span class="sxs-lookup"><span data-stu-id="bf152-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="bf152-107">O `Add` método permite que você use a sintaxe do inicializador de coleção reduzido.</span><span class="sxs-lookup"><span data-stu-id="bf152-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_3.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bf152-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf152-108">See Also</span></span>  
 [<span data-ttu-id="bf152-109">Inicializadores de Coleção</span><span class="sxs-lookup"><span data-stu-id="bf152-109">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [<span data-ttu-id="bf152-110">Como criar um método para adicionar extensão usado por um inicializador de coleção</span><span class="sxs-lookup"><span data-stu-id="bf152-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
