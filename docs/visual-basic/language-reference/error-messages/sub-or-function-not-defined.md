---
title: Sub ou função não definida (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 3a56d5596c79900bb5818a6ed7f8736859b5ea15
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593193"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="24e7a-102">Sub ou função não definida (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24e7a-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="24e7a-103">Um `Sub` ou `Function` deve ser definido para ser chamado.</span><span class="sxs-lookup"><span data-stu-id="24e7a-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="24e7a-104">Possíveis causas do erro incluem:</span><span class="sxs-lookup"><span data-stu-id="24e7a-104">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="24e7a-105">Digitar incorretamente o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="24e7a-105">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="24e7a-106">Tentar chamar um procedimento de outro projeto sem adicionar explicitamente uma referência a esse projeto na **referências** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="24e7a-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="24e7a-107">Especificando um procedimento que não é visível para o procedimento de chamada.</span><span class="sxs-lookup"><span data-stu-id="24e7a-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="24e7a-108">Declarando uma rotina de biblioteca de vínculo dinâmico (DLL) do Windows ou a rotina de recurso de código Macintosh que não está no recurso de biblioteca ou código especificado.</span><span class="sxs-lookup"><span data-stu-id="24e7a-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="24e7a-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="24e7a-109">To correct this error</span></span>  
  
1. <span data-ttu-id="24e7a-110">Certifique-se de que o nome do procedimento esteja escrito corretamente.</span><span class="sxs-lookup"><span data-stu-id="24e7a-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="24e7a-111">Localizar o nome do projeto que contém o procedimento que você deseja chamar o **referências** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="24e7a-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="24e7a-112">Se não aparecer, clique o **procurar** botão para pesquisar por ele.</span><span class="sxs-lookup"><span data-stu-id="24e7a-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="24e7a-113">Marque a caixa de seleção à esquerda do nome do projeto e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="24e7a-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="24e7a-114">Verifique o nome da rotina.</span><span class="sxs-lookup"><span data-stu-id="24e7a-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e7a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24e7a-115">See also</span></span>

- [<span data-ttu-id="24e7a-116">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="24e7a-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="24e7a-117">Gerenciando referências em um projeto</span><span class="sxs-lookup"><span data-stu-id="24e7a-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="24e7a-118">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="24e7a-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="24e7a-119">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="24e7a-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
