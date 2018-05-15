---
title: Não é possível usar parâmetros de tipo como qualificadores
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 563010efc4f3049d330ee2b38b7f59e23292e630
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="70143-102">Não é possível usar parâmetros de tipo como qualificadores</span><span class="sxs-lookup"><span data-stu-id="70143-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="70143-103">Um elemento de programação está qualificado com uma cadeia de caracteres de qualificação que inclui um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="70143-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="70143-104">Um parâmetro de tipo representa um requisito para um tipo que deve ser fornecido quando o tipo genérico é construído.</span><span class="sxs-lookup"><span data-stu-id="70143-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="70143-105">Ele não representa um tipo específico de definidos.</span><span class="sxs-lookup"><span data-stu-id="70143-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="70143-106">Uma cadeia de caracteres de qualificação deve incluir somente os elementos que são definidos em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="70143-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="70143-107">As instruções a seguir podem gerar esse erro.</span><span class="sxs-lookup"><span data-stu-id="70143-107">The following statements can generate this error.</span></span>  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="70143-108">**ID do erro:** BC32098</span><span class="sxs-lookup"><span data-stu-id="70143-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="70143-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="70143-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="70143-110">Remova o parâmetro de tipo de cadeia de caracteres de qualificação ou substituí-lo com um tipo definido.</span><span class="sxs-lookup"><span data-stu-id="70143-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2.  <span data-ttu-id="70143-111">Se você precisar usar um tipo construído para localizar o elemento de programação que está sendo qualificado, você deve usar lógica adicional do programa.</span><span class="sxs-lookup"><span data-stu-id="70143-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70143-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70143-112">See Also</span></span>  
 [<span data-ttu-id="70143-113">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="70143-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="70143-114">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70143-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="70143-115">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="70143-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
