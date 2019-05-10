---
title: O nome do membro de tipo anônimo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: f657048a8aa9748104e40503e727a5e6d90a87ad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646864"
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="39375-102">O nome do membro de tipo anônimo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos</span><span class="sxs-lookup"><span data-stu-id="39375-102">Anonymous type member name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="39375-103">Você não é possível inferir um nome de membro de tipo anônimo de uma expressão complexa.</span><span class="sxs-lookup"><span data-stu-id="39375-103">You cannot infer an anonymous type member name from a complex expression.</span></span>  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 <span data-ttu-id="39375-104">Para obter mais informações sobre fontes das quais os tipos anônimos podem e não é possível inferir os tipos e nomes de membros, consulte [como: Inferir nomes de propriedade e tipos em declarações de tipo anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span><span class="sxs-lookup"><span data-stu-id="39375-104">For more information about sources from which anonymous types can and cannot infer member names and types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
 <span data-ttu-id="39375-105">**ID do erro:** BC36556</span><span class="sxs-lookup"><span data-stu-id="39375-105">**Error ID:** BC36556</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="39375-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="39375-106">To correct this error</span></span>  
  
- <span data-ttu-id="39375-107">Atribua a expressão a um nome de membro, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="39375-107">Assign the expression to a member name, as shown in the following code:</span></span>  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="39375-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39375-108">See also</span></span>

- [<span data-ttu-id="39375-109">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="39375-109">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="39375-110">Como: Inferir nomes de propriedade e tipos em declarações de tipo anônimo</span><span class="sxs-lookup"><span data-stu-id="39375-110">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
