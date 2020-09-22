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
ms.openlocfilehash: 8dfd830e4c7ed97c8813da4ad310ee59b26f44f8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90868800"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="b787b-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b787b-102">Ansi (Visual Basic)</span></span>

<span data-ttu-id="b787b-103">Especifica que Visual Basic deve realizar marshaling de todas as cadeias de caracteres para valores de American National Standards Institute (ANSI), independentemente do nome do procedimento externo que está sendo declarado.</span><span class="sxs-lookup"><span data-stu-id="b787b-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="b787b-104">Quando você chama um procedimento definido fora do seu projeto, o compilador Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente.</span><span class="sxs-lookup"><span data-stu-id="b787b-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="b787b-105">Essas informações incluem onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o conjunto de caracteres da cadeia de caracteres que ele usa.</span><span class="sxs-lookup"><span data-stu-id="b787b-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="b787b-106">A [instrução Declare](../statements/declare-statement.md) cria uma referência a um procedimento externo e fornece essas informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="b787b-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="b787b-107">A `charsetmodifier` parte na `Declare` instrução fornece as informações do conjunto de caracteres para o marshaling de cadeias durante uma chamada para o procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="b787b-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="b787b-108">Ele também afeta como Visual Basic pesquisa o nome do procedimento externo no arquivo externo.</span><span class="sxs-lookup"><span data-stu-id="b787b-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="b787b-109">O `Ansi` modificador especifica que Visual Basic deve empacotar todas as cadeias de caracteres para valores ANSI e deve procurar o procedimento sem modificar seu nome durante a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b787b-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="b787b-110">Se nenhum modificador de conjunto de caracteres for especificado, `Ansi` será o padrão.</span><span class="sxs-lookup"><span data-stu-id="b787b-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b787b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b787b-111">Remarks</span></span>  

 <span data-ttu-id="b787b-112">O `Ansi` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="b787b-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="b787b-113">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="b787b-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="b787b-114">Notas para desenvolvedores de dispositivos inteligentes</span><span class="sxs-lookup"><span data-stu-id="b787b-114">Smart Device Developer Notes</span></span>  

 <span data-ttu-id="b787b-115">Não há suporte para essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b787b-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b787b-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="b787b-116">See also</span></span>

- [<span data-ttu-id="b787b-117">Automático</span><span class="sxs-lookup"><span data-stu-id="b787b-117">Auto</span></span>](auto.md)
- [<span data-ttu-id="b787b-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="b787b-118">Unicode</span></span>](unicode.md)
- [<span data-ttu-id="b787b-119">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="b787b-119">Keywords</span></span>](../keywords/index.md)
