---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 042908b8427de2de0de96bbb32df7be018bb915c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="c6288-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6288-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="c6288-103">Especifica que o Visual Basic deve empacotar todas as cadeias de caracteres para valores Unicode, independentemente do nome do procedimento externo que está sendo declarado.</span><span class="sxs-lookup"><span data-stu-id="c6288-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="c6288-104">Quando você chama um procedimento definido fora do seu projeto, o compilador do Visual Basic não tem acesso às informações que ele deve ter para chamar o procedimento corretamente.</span><span class="sxs-lookup"><span data-stu-id="c6288-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="c6288-105">Essa informação inclui onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno, e a cadeia de caracteres do conjunto de caracteres ele usa.</span><span class="sxs-lookup"><span data-stu-id="c6288-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="c6288-106">O [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece esta informação necessária.</span><span class="sxs-lookup"><span data-stu-id="c6288-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="c6288-107">O `charsetmodifier` no `Declare` instrução fornece as informações do conjunto de caracteres para empacotar cadeias de caracteres durante a chamada ao procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="c6288-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="c6288-108">Isso também afeta como o Visual Basic procura o arquivo externo para o nome do procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="c6288-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="c6288-109">O `Unicode` modificador Especifica que o Visual Basic deve realizar marshaling de todas as cadeias de caracteres para valores Unicode e deve consultar o procedimento sem modificar seu nome durante a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c6288-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="c6288-110">Se nenhum modificador de conjunto de caracteres for especificada, `Ansi` é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c6288-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6288-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6288-111">Remarks</span></span>  
 <span data-ttu-id="c6288-112">O `Unicode` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="c6288-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="c6288-113">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="c6288-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="c6288-114">Notas do desenvolvedor de dispositivo inteligente</span><span class="sxs-lookup"><span data-stu-id="c6288-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="c6288-115">Não há suporte para esta palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="c6288-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6288-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6288-116">See Also</span></span>  
 [<span data-ttu-id="c6288-117">Ansi</span><span class="sxs-lookup"><span data-stu-id="c6288-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [<span data-ttu-id="c6288-118">Auto</span><span class="sxs-lookup"><span data-stu-id="c6288-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="c6288-119">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="c6288-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
