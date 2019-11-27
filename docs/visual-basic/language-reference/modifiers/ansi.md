---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 0c38c2b81af7b4cb8fd1723853a09c5413f805af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344734"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="7ddc4-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ddc4-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="7ddc4-103">Especifica que Visual Basic deve realizar marshaling de todas as cadeias de caracteres para valores de American National Standards Institute (ANSI), independentemente do nome do procedimento externo que está sendo declarado.</span><span class="sxs-lookup"><span data-stu-id="7ddc4-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="7ddc4-104">Quando você chama um procedimento definido fora do seu projeto, o compilador Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente.</span><span class="sxs-lookup"><span data-stu-id="7ddc4-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="7ddc4-105">Essas informações incluem onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o conjunto de caracteres da cadeia de caracteres que ele usa.</span><span class="sxs-lookup"><span data-stu-id="7ddc4-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="7ddc4-106">A [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece essas informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="7ddc4-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="7ddc4-107">A parte `charsetmodifier` na instrução `Declare` fornece as informações de um conjunto de caracteres para o marshaling de cadeias durante uma chamada para o procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="7ddc4-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="7ddc4-108">Ele também afeta como Visual Basic pesquisa o nome do procedimento externo no arquivo externo.</span><span class="sxs-lookup"><span data-stu-id="7ddc4-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="7ddc4-109">O modificador de `Ansi` especifica que Visual Basic deve realizar marshaling de todas as cadeias de caracteres para valores ANSI e deve procurar o procedimento sem modificar seu nome durante a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="7ddc4-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="7ddc4-110">Se nenhum modificador de conjunto de caracteres for especificado, `Ansi` será o padrão.</span><span class="sxs-lookup"><span data-stu-id="7ddc4-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ddc4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ddc4-111">Remarks</span></span>  
 <span data-ttu-id="7ddc4-112">O modificador de `Ansi` pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="7ddc4-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="7ddc4-113">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="7ddc4-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="7ddc4-114">Notas para desenvolvedores de dispositivos inteligentes</span><span class="sxs-lookup"><span data-stu-id="7ddc4-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="7ddc4-115">Não há suporte para essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="7ddc4-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ddc4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ddc4-116">See also</span></span>

- [<span data-ttu-id="7ddc4-117">Auto</span><span class="sxs-lookup"><span data-stu-id="7ddc4-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="7ddc4-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="7ddc4-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="7ddc4-119">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="7ddc4-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
