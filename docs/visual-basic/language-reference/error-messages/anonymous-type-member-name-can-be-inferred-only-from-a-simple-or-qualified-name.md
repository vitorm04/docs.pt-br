---
title: O nome do membro de tipo anônimo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: 38f669fe183ac79ebed6e5a122bc70aedc9bb753
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701223"
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="d42b4-102">O nome do membro de tipo anônimo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos</span><span class="sxs-lookup"><span data-stu-id="d42b4-102">Anonymous type member name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="d42b4-103">Não é possível inferir um nome de membro de tipo anônimo de uma expressão complexa.</span><span class="sxs-lookup"><span data-stu-id="d42b4-103">You cannot infer an anonymous type member name from a complex expression.</span></span>  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 <span data-ttu-id="d42b4-104">Para obter mais informações sobre fontes das quais tipos anônimos podem e não podem inferir nomes e tipos de membros, consulte [How para: Inferir nomes e tipos de propriedade em declarações de tipo anônimos @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="d42b4-104">For more information about sources from which anonymous types can and cannot infer member names and types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
 <span data-ttu-id="d42b4-105">**ID do erro:** BC36556</span><span class="sxs-lookup"><span data-stu-id="d42b4-105">**Error ID:** BC36556</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d42b4-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d42b4-106">To correct this error</span></span>  
  
- <span data-ttu-id="d42b4-107">Atribua a expressão a um nome de membro, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="d42b4-107">Assign the expression to a member name, as shown in the following code:</span></span>  
  
    ```vb  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d42b4-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d42b4-108">See also</span></span>

- [<span data-ttu-id="d42b4-109">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="d42b4-109">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- <span data-ttu-id="d42b4-110">[Como: Inferir nomes e tipos de propriedade em declarações de tipo anônimo @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="d42b4-110">[How to: Infer Property Names and Types in Anonymous Type Declarations](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>
