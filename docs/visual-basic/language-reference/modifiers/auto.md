---
title: Automático
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 7ea46e5f8b882bb986f23e792b240bad0c5be7a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351614"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="fedee-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fedee-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="fedee-103">Especifica que Visual Basic deve empacotar cadeias de caracteres de acordo com .NET Framework regras com base no nome externo do procedimento externo que está sendo declarado.</span><span class="sxs-lookup"><span data-stu-id="fedee-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="fedee-104">Quando você chama um procedimento definido fora do seu projeto, o compilador Visual Basic não tem acesso às informações que ele deve ter para chamar o procedimento corretamente.</span><span class="sxs-lookup"><span data-stu-id="fedee-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="fedee-105">Essas informações incluem onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o conjunto de caracteres da cadeia de caracteres que ele usa.</span><span class="sxs-lookup"><span data-stu-id="fedee-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="fedee-106">A [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece essas informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="fedee-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="fedee-107">A parte `charsetmodifier` na instrução `Declare` fornece as informações de um conjunto de caracteres para o marshaling de cadeias durante uma chamada para o procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="fedee-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="fedee-108">Ele também afeta como Visual Basic pesquisa o nome do procedimento externo no arquivo externo.</span><span class="sxs-lookup"><span data-stu-id="fedee-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="fedee-109">O modificador de `Auto` especifica que Visual Basic deve realizar marshaling de cadeia de caracteres de acordo com as regras de .NET Framework e que ele deve determinar o conjunto de caractere base da plataforma de tempo de execução e possivelmente modificar o nome do procedimento externo se a pesquisa inicial falhar.</span><span class="sxs-lookup"><span data-stu-id="fedee-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="fedee-110">Para obter mais informações, consulte "conjuntos de caracteres" na [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fedee-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="fedee-111">Se nenhum modificador de conjunto de caracteres for especificado, `Ansi` será o padrão.</span><span class="sxs-lookup"><span data-stu-id="fedee-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fedee-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="fedee-112">Remarks</span></span>  
 <span data-ttu-id="fedee-113">O modificador de `Auto` pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="fedee-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="fedee-114">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="fedee-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="fedee-115">Notas para desenvolvedores de dispositivos inteligentes</span><span class="sxs-lookup"><span data-stu-id="fedee-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="fedee-116">Não há suporte para essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="fedee-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fedee-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fedee-117">See also</span></span>

- [<span data-ttu-id="fedee-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="fedee-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="fedee-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="fedee-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="fedee-120">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="fedee-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
