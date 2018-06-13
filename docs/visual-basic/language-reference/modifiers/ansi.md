---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: c7037acac58de56a396bd89f595ef897743ff4e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595073"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="d2a93-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2a93-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="d2a93-103">Especifica que o Visual Basic deve empacotar todas as cadeias de caracteres para valores American National Standards Institute (ANSI), independentemente do nome do procedimento externo que está sendo declarado.</span><span class="sxs-lookup"><span data-stu-id="d2a93-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="d2a93-104">Quando você chama um procedimento definido fora do seu projeto, o compilador do Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente.</span><span class="sxs-lookup"><span data-stu-id="d2a93-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="d2a93-105">Essa informação inclui onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno, e a cadeia de caracteres do conjunto de caracteres ele usa.</span><span class="sxs-lookup"><span data-stu-id="d2a93-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="d2a93-106">O [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece esta informação necessária.</span><span class="sxs-lookup"><span data-stu-id="d2a93-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="d2a93-107">O `charsetmodifier` no `Declare` instrução fornece as informações de conjunto de caracteres para empacotar cadeias de caracteres durante a chamada ao procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="d2a93-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="d2a93-108">Isso também afeta como o Visual Basic procura o arquivo externo para o nome do procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="d2a93-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="d2a93-109">O `Ansi` modificador Especifica que o Visual Basic deve realizar marshaling de todas as cadeias de caracteres para valores ANSI e deve consultar o procedimento sem modificar seu nome durante a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="d2a93-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="d2a93-110">Se nenhum modificador de conjunto de caracteres for especificada, `Ansi` é o padrão.</span><span class="sxs-lookup"><span data-stu-id="d2a93-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2a93-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d2a93-111">Remarks</span></span>  
 <span data-ttu-id="d2a93-112">O `Ansi` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="d2a93-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="d2a93-113">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="d2a93-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="d2a93-114">Notas do desenvolvedor de dispositivo inteligente</span><span class="sxs-lookup"><span data-stu-id="d2a93-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="d2a93-115">Não há suporte para esta palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="d2a93-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a93-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2a93-116">See Also</span></span>  
 [<span data-ttu-id="d2a93-117">Auto</span><span class="sxs-lookup"><span data-stu-id="d2a93-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="d2a93-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="d2a93-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="d2a93-119">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="d2a93-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
