---
title: Como criar uma coleção usada por um inicializador de coleção
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 5eaf9e828455bf2accda86ab52a1ce645f10b9ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349057"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="405d3-102">Como criar uma coleção usada por um inicializador de coleção (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="405d3-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="405d3-103">Quando você usa um inicializador de coleção para criar uma coleção, o compilador Visual Basic procura um método `Add` do tipo de coleção para o qual os parâmetros do método `Add` correspondem aos tipos de valores no inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="405d3-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="405d3-104">Esse método de `Add` é usado para popular a coleção com os valores do inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="405d3-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="405d3-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="405d3-105">Example</span></span>  
 <span data-ttu-id="405d3-106">O exemplo a seguir mostra uma coleção de `OrderCollection` que contém um método público `Add` que um inicializador de coleção pode usar para adicionar objetos do tipo `Order`.</span><span class="sxs-lookup"><span data-stu-id="405d3-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="405d3-107">O método `Add` permite que você use a sintaxe de inicializador de coleção reduzida.</span><span class="sxs-lookup"><span data-stu-id="405d3-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="405d3-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="405d3-108">See also</span></span>

- [<span data-ttu-id="405d3-109">Inicializadores de Coleção</span><span class="sxs-lookup"><span data-stu-id="405d3-109">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="405d3-110">Como criar um método para adicionar extensão usado por um inicializador de coleção</span><span class="sxs-lookup"><span data-stu-id="405d3-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
