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
ms.openlocfilehash: e4beb320b3aa0cadb790dd3ab92255496bc32f05
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802694"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="70e75-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70e75-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="70e75-103">Especifica que Visual Basic deve realizar marshaling de cadeias de caracteres de acordo com as regras do .NET Framework com base no nome externo do procedimento externo que está sendo declarado.</span><span class="sxs-lookup"><span data-stu-id="70e75-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="70e75-104">Quando você chama um procedimento definido fora de seu projeto, o compilador do Visual Basic não tem acesso às informações que ele deve ter para chamar o procedimento corretamente.</span><span class="sxs-lookup"><span data-stu-id="70e75-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="70e75-105">Essas informações incluem onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o caractere da cadeia de caracteres conjunto que ele usa.</span><span class="sxs-lookup"><span data-stu-id="70e75-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="70e75-106">O [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece esta informação necessária.</span><span class="sxs-lookup"><span data-stu-id="70e75-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="70e75-107">O `charsetmodifier` parte o `Declare` instrução fornece a informação do conjunto de caracteres de marshaling de cadeias de caracteres durante uma chamada ao procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="70e75-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="70e75-108">Isso também afeta como o Visual Basic procura o arquivo externo para o nome do procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="70e75-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="70e75-109">O `Auto` modificador Especifica Visual Basic deve realizar marshaling de cadeias de caracteres de acordo com as regras do .NET Framework e que deve determinar o caractere base definido da plataforma de tempo de execução e possivelmente modificar o nome do procedimento externo se inicial de pesquisa falhará.</span><span class="sxs-lookup"><span data-stu-id="70e75-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="70e75-110">Para obter mais informações, consulte "Conjuntos de caracteres" na [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="70e75-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="70e75-111">Se nenhum modificador de conjunto de caracteres for especificado, `Ansi` é o padrão.</span><span class="sxs-lookup"><span data-stu-id="70e75-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70e75-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="70e75-112">Remarks</span></span>  
 <span data-ttu-id="70e75-113">O `Auto` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="70e75-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="70e75-114">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="70e75-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="70e75-115">Notas do desenvolvedor de dispositivo inteligente</span><span class="sxs-lookup"><span data-stu-id="70e75-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="70e75-116">Não há suporte para essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="70e75-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70e75-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70e75-117">See also</span></span>

- [<span data-ttu-id="70e75-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="70e75-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="70e75-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="70e75-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="70e75-120">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="70e75-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
