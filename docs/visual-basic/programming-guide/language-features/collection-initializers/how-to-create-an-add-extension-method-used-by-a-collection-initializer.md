---
title: 'Como: Criar um método para Adicionar extensão usado por um inicializador de coleção (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 458421da70aca6728f3f03945c28b4c988e44ad7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978534"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="25690-102">Como: Criar um método para Adicionar extensão usado por um inicializador de coleção (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25690-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="25690-103">Quando você usa um inicializador de coleção para criar uma coleção, o compilador do Visual Basic procura um `Add` método de tipo de coleção para a qual os parâmetros para o `Add` método correspondem aos tipos dos valores no inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="25690-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="25690-104">Isso `Add` método é usado para popular a coleção com os valores do inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="25690-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="25690-105">Se nenhuma correspondência `Add` método existe e você não pode modificar o código para a coleção, você pode adicionar um método de extensão chamado `Add` que usa os parâmetros que são necessários para o inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="25690-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="25690-106">Isso normalmente é o que você precisa fazer ao usar inicializadores de coleção para coleções genéricas.</span><span class="sxs-lookup"><span data-stu-id="25690-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25690-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="25690-107">Example</span></span>  
 <span data-ttu-id="25690-108">O exemplo a seguir mostra como adicionar um método de extensão para o genérico <xref:System.Collections.Generic.List%601> tipo de forma que um inicializador de coleção pode ser usado para adicionar objetos do tipo `Employee`.</span><span class="sxs-lookup"><span data-stu-id="25690-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="25690-109">O método de extensão permite que você use a sintaxe do inicializador de coleção reduzida.</span><span class="sxs-lookup"><span data-stu-id="25690-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="25690-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25690-110">See also</span></span>
- [<span data-ttu-id="25690-111">Inicializadores de Coleção</span><span class="sxs-lookup"><span data-stu-id="25690-111">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="25690-112">Como: Criar uma coleção usada por um inicializador de coleção</span><span class="sxs-lookup"><span data-stu-id="25690-112">How to: Create a Collection Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
