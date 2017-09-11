---
title: "Como: criar um método para Adicionar extensão usado por um inicializador de coleção (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4e3fe581e2b124517f4638d8b7b3c3fd3f3ecb74
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="bc358-102">Como criar um método para adicionar extensão usado por um inicializador de coleção (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc358-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="bc358-103">Quando você usa um inicializador de coleção para criar uma coleção, o compilador do Visual Basic procura um `Add` método do tipo de coleção para a qual os parâmetros para o `Add` método correspondem aos tipos de valores no inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="bc358-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="bc358-104">Isso `Add` método é usado para preencher a coleção com os valores do inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="bc358-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="bc358-105">Se nenhuma correspondência `Add` método existe e não é possível modificar o código para a coleção, você pode adicionar um método de extensão chamado `Add` que usa os parâmetros necessários para o inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="bc358-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="bc358-106">Isso normalmente é o que você precisa fazer quando você usa os inicializadores de coleção para coleções genéricas.</span><span class="sxs-lookup"><span data-stu-id="bc358-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc358-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc358-107">Example</span></span>  
 <span data-ttu-id="bc358-108">O exemplo a seguir mostra como adicionar um método de extensão para genérica <xref:System.Collections.Generic.List%601>tipo de forma que um inicializador de coleção pode ser usado para adicionar objetos do tipo `Employee`.</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="bc358-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="bc358-109">O método de extensão permite que você use a sintaxe do inicializador de coleção reduzido.</span><span class="sxs-lookup"><span data-stu-id="bc358-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 <span data-ttu-id="bc358-110">[!code-vb[VbVbalrCollectionInitializersHowTo1 n º&1;](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="bc358-110">[!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]</span></span>  
  
 <span data-ttu-id="bc358-111">[!code-vb[VbVbalrCollectionInitializersHowTo1 n º&2;](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="bc358-111">[!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]</span></span>  
  
 <span data-ttu-id="bc358-112">[!code-vb[VbVbalrCollectionInitializersHowTo1 n º&3;](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="bc358-112">[!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc358-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc358-113">See Also</span></span>  
 <span data-ttu-id="bc358-114">[Inicializadores de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md) </span><span class="sxs-lookup"><span data-stu-id="bc358-114">[Collection Initializers](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md) </span></span>  
<span data-ttu-id="bc358-115"> [Como criar uma coleção usada por um inicializador de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)</span><span class="sxs-lookup"><span data-stu-id="bc358-115"> [How to: Create a Collection Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)</span></span>
