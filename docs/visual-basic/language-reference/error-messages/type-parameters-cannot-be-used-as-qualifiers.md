---
title: Não é possível usar parâmetros de tipo como qualificadores
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 3ff4b189539bf119351a94dabadd596c336ac723
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250339"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="caf35-102">Não é possível usar parâmetros de tipo como qualificadores</span><span class="sxs-lookup"><span data-stu-id="caf35-102">Type parameters cannot be used as qualifiers</span></span>

<span data-ttu-id="caf35-103">Um elemento de programação é qualificado com uma cadeia de caracteres de qualificação que inclui um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="caf35-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>

<span data-ttu-id="caf35-104">Um parâmetro de tipo representa um requisito para um tipo que deve ser fornecido quando o tipo genérico é construído.</span><span class="sxs-lookup"><span data-stu-id="caf35-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="caf35-105">Ele não representa um tipo definido específico.</span><span class="sxs-lookup"><span data-stu-id="caf35-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="caf35-106">Uma cadeia de caracteres de qualificação deve incluir apenas elementos que são definidos no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="caf35-106">A qualification string must include only elements that are defined at compile time.</span></span>

<span data-ttu-id="caf35-107">O código a seguir pode gerar esse erro:</span><span class="sxs-lookup"><span data-stu-id="caf35-107">The following code can generate this error:</span></span>

```vb  
Public Function CheckText(Of c As System.Windows.Forms.Control)(
    badText As String) As Boolean
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.
End Function  
```  
  
 <span data-ttu-id="caf35-108">**ID do erro:** BC32098</span><span class="sxs-lookup"><span data-stu-id="caf35-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="caf35-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="caf35-109">To correct this error</span></span>  
  
1. <span data-ttu-id="caf35-110">Remova o parâmetro de tipo da cadeia de caracteres de qualificação ou substitua-o por um tipo definido.</span><span class="sxs-lookup"><span data-stu-id="caf35-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2. <span data-ttu-id="caf35-111">Se você precisar usar um tipo construído para localizar o elemento de programação que está sendo qualificado, deverá usar a lógica de programa adicional.</span><span class="sxs-lookup"><span data-stu-id="caf35-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caf35-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="caf35-112">See also</span></span>

- [<span data-ttu-id="caf35-113">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="caf35-113">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="caf35-114">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="caf35-114">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="caf35-115">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="caf35-115">Type List</span></span>](../statements/type-list.md)
