---
title: Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: c4286ed9e9d5fd768ae29b7050b3d1505ccca9dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344218"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="61e9f-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61e9f-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="61e9f-103">Especifica que Visual Basic deve realizar marshaling de todas as cadeias de caracteres para valores Unicode, independentemente do nome do procedimento externo que está sendo declarado.</span><span class="sxs-lookup"><span data-stu-id="61e9f-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="61e9f-104">Quando você chama um procedimento definido fora do seu projeto, o compilador Visual Basic não tem acesso às informações que ele deve ter para chamar o procedimento corretamente.</span><span class="sxs-lookup"><span data-stu-id="61e9f-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="61e9f-105">Essas informações incluem onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o conjunto de caracteres da cadeia de caracteres que ele usa.</span><span class="sxs-lookup"><span data-stu-id="61e9f-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="61e9f-106">A [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece essas informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="61e9f-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="61e9f-107">A parte `charsetmodifier` na instrução `Declare` fornece as informações do conjunto de caracteres para empacotar as cadeias durante uma chamada para o procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="61e9f-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="61e9f-108">Ele também afeta como Visual Basic pesquisa o nome do procedimento externo no arquivo externo.</span><span class="sxs-lookup"><span data-stu-id="61e9f-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="61e9f-109">O modificador de `Unicode` especifica que Visual Basic deve realizar marshaling de todas as cadeias de caracteres para valores Unicode e deve procurar o procedimento sem modificar seu nome durante a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="61e9f-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="61e9f-110">Se nenhum modificador de conjunto de caracteres for especificado, `Ansi` será o padrão.</span><span class="sxs-lookup"><span data-stu-id="61e9f-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61e9f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="61e9f-111">Remarks</span></span>  
 <span data-ttu-id="61e9f-112">O modificador de `Unicode` pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="61e9f-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="61e9f-113">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="61e9f-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="61e9f-114">Notas para desenvolvedores de dispositivos inteligentes</span><span class="sxs-lookup"><span data-stu-id="61e9f-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="61e9f-115">Não há suporte para essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="61e9f-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e9f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61e9f-116">See also</span></span>

- [<span data-ttu-id="61e9f-117">Ansi</span><span class="sxs-lookup"><span data-stu-id="61e9f-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="61e9f-118">Auto</span><span class="sxs-lookup"><span data-stu-id="61e9f-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="61e9f-119">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="61e9f-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
