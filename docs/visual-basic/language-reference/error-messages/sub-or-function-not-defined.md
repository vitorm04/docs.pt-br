---
title: Sub ou Function não definida
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 8b81460eccb6be8baa2ea7bc68d0f80c9d16398e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349573"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="44594-102">Sub ou função não definida (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44594-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="44594-103">Um `Sub` ou `Function` deve ser definido para ser chamado.</span><span class="sxs-lookup"><span data-stu-id="44594-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="44594-104">Possíveis causas do erro incluem:</span><span class="sxs-lookup"><span data-stu-id="44594-104">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="44594-105">Digitação incorreta do nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="44594-105">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="44594-106">Tentativa de chamar um procedimento de outro projeto sem adicionar explicitamente uma referência a esse projeto na caixa de diálogo **referências** .</span><span class="sxs-lookup"><span data-stu-id="44594-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="44594-107">Especificar um procedimento que não seja visível para o procedimento de chamada.</span><span class="sxs-lookup"><span data-stu-id="44594-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="44594-108">Declarando uma rotina DLL (biblioteca de vínculo dinâmico) do Windows ou uma rotina de recurso de código do Macintosh que não está na biblioteca ou no recurso de código especificado.</span><span class="sxs-lookup"><span data-stu-id="44594-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="44594-109">Para corrigir esse erro</span><span class="sxs-lookup"><span data-stu-id="44594-109">To correct this error</span></span>  
  
1. <span data-ttu-id="44594-110">Verifique se o nome do procedimento está escrito corretamente.</span><span class="sxs-lookup"><span data-stu-id="44594-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="44594-111">Localize o nome do projeto que contém o procedimento que você deseja chamar na caixa de diálogo **referências** .</span><span class="sxs-lookup"><span data-stu-id="44594-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="44594-112">Se não aparecer, clique no botão **procurar** para procurá-lo.</span><span class="sxs-lookup"><span data-stu-id="44594-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="44594-113">Marque a caixa de seleção à esquerda do nome do projeto e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="44594-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="44594-114">Verifique o nome da rotina.</span><span class="sxs-lookup"><span data-stu-id="44594-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44594-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44594-115">See also</span></span>

- [<span data-ttu-id="44594-116">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="44594-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="44594-117">Gerenciando referências em um projeto</span><span class="sxs-lookup"><span data-stu-id="44594-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="44594-118">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="44594-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="44594-119">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="44594-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
