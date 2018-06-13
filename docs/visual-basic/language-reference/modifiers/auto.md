---
title: Auto (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 414998b4bef526060e7ba4f584fa071fbd0acaa5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595869"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="d333d-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d333d-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="d333d-103">Especifica que Visual Basic deve realizar marshaling de cadeias de caracteres de acordo com as regras do .NET Framework com base no nome externo do procedimento externo que está sendo declarado.</span><span class="sxs-lookup"><span data-stu-id="d333d-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="d333d-104">Quando você chama um procedimento definido fora do seu projeto, o compilador do Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente.</span><span class="sxs-lookup"><span data-stu-id="d333d-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="d333d-105">Essa informação inclui onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno, e a cadeia de caracteres do conjunto de caracteres ele usa.</span><span class="sxs-lookup"><span data-stu-id="d333d-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="d333d-106">O [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece esta informação necessária.</span><span class="sxs-lookup"><span data-stu-id="d333d-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="d333d-107">O `charsetmodifier` no `Declare` instrução fornece as informações de conjunto de caracteres para empacotar cadeias de caracteres durante a chamada ao procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="d333d-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="d333d-108">Isso também afeta como o Visual Basic procura o arquivo externo para o nome do procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="d333d-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="d333d-109">O `Auto` modificador Especifica Visual Basic deve realizar marshaling de cadeias de caracteres de acordo com as regras do .NET Framework e que ele deve determinar o caractere de base definido da plataforma de tempo de execução e possivelmente modificar o nome do procedimento externo se inicial de pesquisa falhará.</span><span class="sxs-lookup"><span data-stu-id="d333d-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="d333d-110">Para obter mais informações, consulte "Conjuntos de caracteres" [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d333d-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="d333d-111">Se nenhum modificador de conjunto de caracteres for especificada, `Ansi` é o padrão.</span><span class="sxs-lookup"><span data-stu-id="d333d-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d333d-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="d333d-112">Remarks</span></span>  
 <span data-ttu-id="d333d-113">O `Auto` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="d333d-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="d333d-114">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="d333d-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="d333d-115">Notas do desenvolvedor de dispositivo inteligente</span><span class="sxs-lookup"><span data-stu-id="d333d-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="d333d-116">Não há suporte para esta palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="d333d-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d333d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d333d-117">See Also</span></span>  
 [<span data-ttu-id="d333d-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="d333d-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [<span data-ttu-id="d333d-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="d333d-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="d333d-120">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="d333d-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
