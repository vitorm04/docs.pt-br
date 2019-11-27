---
title: Como criar um método para adicionar extensão usado por um inicializador de coleção
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 6d5f9d38b413b79f111a14ec3829c57a9797ce54
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346721"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="4bbe1-102">Como criar um método para adicionar extensão usado por um inicializador de coleção (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4bbe1-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="4bbe1-103">Quando você usa um inicializador de coleção para criar uma coleção, o compilador Visual Basic procura um método `Add` do tipo de coleção para o qual os parâmetros do método `Add` correspondem aos tipos de valores no inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="4bbe1-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="4bbe1-104">Esse método de `Add` é usado para popular a coleção com os valores do inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="4bbe1-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="4bbe1-105">Se nenhum método de `Add` correspondente existir e você não puder modificar o código para a coleção, você poderá adicionar um método de extensão chamado `Add` que usa os parâmetros exigidos pelo inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="4bbe1-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="4bbe1-106">Normalmente, isso é o que você precisa fazer quando usa inicializadores de coleção para coleções genéricas.</span><span class="sxs-lookup"><span data-stu-id="4bbe1-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bbe1-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4bbe1-107">Example</span></span>  
 <span data-ttu-id="4bbe1-108">O exemplo a seguir mostra como adicionar um método de extensão ao tipo de <xref:System.Collections.Generic.List%601> genérico para que um inicializador de coleção possa ser usado para adicionar objetos do tipo `Employee`.</span><span class="sxs-lookup"><span data-stu-id="4bbe1-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="4bbe1-109">O método de extensão permite que você use a sintaxe de inicializador de coleção abreviada.</span><span class="sxs-lookup"><span data-stu-id="4bbe1-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="4bbe1-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bbe1-110">See also</span></span>

- [<span data-ttu-id="4bbe1-111">Inicializadores de Coleção</span><span class="sxs-lookup"><span data-stu-id="4bbe1-111">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="4bbe1-112">Como criar uma coleção usada por um inicializador de coleção</span><span class="sxs-lookup"><span data-stu-id="4bbe1-112">How to: Create a Collection Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
