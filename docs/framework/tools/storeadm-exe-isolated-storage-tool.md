---
title: Storeadm.exe (Ferramenta de Armazenamento Isolado)
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 906d9d4dfd1c1082a4b49b7143f590967dcc7fd0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092260"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="eb4c3-102">Storeadm.exe (Ferramenta de Armazenamento Isolado)</span><span class="sxs-lookup"><span data-stu-id="eb4c3-102">Storeadm.exe (Isolated Storage Tool)</span></span>
<span data-ttu-id="eb4c3-103">A ferramenta Armazenamento Isolado lista ou remove todos os repositórios existentes para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-103">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="eb4c3-104">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="eb4c3-105">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="eb4c3-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="eb4c3-106">Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="eb4c3-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="eb4c3-107">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="eb4c3-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb4c3-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb4c3-108">Syntax</span></span>  
  
```  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb4c3-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eb4c3-109">Parameters</span></span>  
  
|<span data-ttu-id="eb4c3-110">Opção</span><span class="sxs-lookup"><span data-stu-id="eb4c3-110">Option</span></span>|<span data-ttu-id="eb4c3-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb4c3-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="eb4c3-112">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="eb4c3-112">**/h**[**elp**]</span></span>|<span data-ttu-id="eb4c3-113">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-113">Displays command syntax and options for the tool.</span></span>|  
|**<span data-ttu-id="eb4c3-114">/list</span><span class="sxs-lookup"><span data-stu-id="eb4c3-114">/list</span></span>**|<span data-ttu-id="eb4c3-115">Exibe todos os repositórios existentes para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-115">Displays all existing stores for the current user.</span></span> <span data-ttu-id="eb4c3-116">Isso inclui os repositórios de todos os aplicativos ou assemblies executados por esse usuário.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-116">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|**<span data-ttu-id="eb4c3-117">/machine</span><span class="sxs-lookup"><span data-stu-id="eb4c3-117">/machine</span></span>**|<span data-ttu-id="eb4c3-118">Seleciona o repositório do computador.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-118">Selects the machine store.</span></span> <span data-ttu-id="eb4c3-119">Use essa opção com as opções **/list** ou **/remove** para especificar que a ação deve ser aplicada ao repositório do computador.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-119">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="eb4c3-120">Novidades no .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="eb4c3-120">New in the .NET Framework 2.0</span></span>|  
|**<span data-ttu-id="eb4c3-121">/quiet</span><span class="sxs-lookup"><span data-stu-id="eb4c3-121">/quiet</span></span>**|<span data-ttu-id="eb4c3-122">Especifica o modo silencioso; suprime a saída informativa de forma que apenas as mensagens de erro sejam exibidas.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-122">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|**<span data-ttu-id="eb4c3-123">/remove</span><span class="sxs-lookup"><span data-stu-id="eb4c3-123">/remove</span></span>**|<span data-ttu-id="eb4c3-124">Remove permanentemente todos os repositórios existentes para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-124">Permanently removes all existing stores for the current user.</span></span>|  
|**<span data-ttu-id="eb4c3-125">/roaming</span><span class="sxs-lookup"><span data-stu-id="eb4c3-125">/roaming</span></span>**|<span data-ttu-id="eb4c3-126">Seleciona o repositório móvel.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-126">Selects the roaming store.</span></span> <span data-ttu-id="eb4c3-127">Use essa opção com as opções **/list** ou **/remove** para especificar que a ação deve ser aplicada ao repositório móvel.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-127">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|**<span data-ttu-id="eb4c3-128">/?</span><span class="sxs-lookup"><span data-stu-id="eb4c3-128">/?</span></span>**|<span data-ttu-id="eb4c3-129">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-129">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb4c3-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb4c3-130">Remarks</span></span>  
 <span data-ttu-id="eb4c3-131">A execução de Storeadm.exe na linha de comando sem especificar nenhuma opção exibe a sintaxe e as opções da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-131">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="eb4c3-132">As opções **/list** e **/remove** costumam ser usadas uma de cada vez; no entanto, se duas ou mais opções forem especificadas, elas serão realizadas na ordem em que são exibidas na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-132">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="eb4c3-133">Os aplicativos têm uma opção de gravação em um dos dois repositórios para um usuário ou no repositório do computador:</span><span class="sxs-lookup"><span data-stu-id="eb4c3-133">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
-   <span data-ttu-id="eb4c3-134">O repositório local existe em um local que tem garantia de não ser compatível com roaming (no Windows 2000 e posteriores), mesmo se o roaming de dados do usuário estiver habilitado para o usuário.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-134">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
-   <span data-ttu-id="eb4c3-135">O repositório móvel existe em um local compatível com roaming, mas só poderá fazer isso se o roaming estiver habilitado para o usuário por meio da administração do Windows NT.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-135">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
-   <span data-ttu-id="eb4c3-136">O repositório do computador é comum a todos os usuários em um computador e é armazenado em um diretório comum nesse computador.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-136">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb4c3-137">O repositório do computador é novo na versão 2.0 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-137">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="eb4c3-138">Independentemente do roaming estar efetivamente habilitado para o usuário, isso não afeta a administração de Storeadm.exe.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-138">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="eb4c3-139">A execução da ferramenta sem opções se aplica a todas as ações no repositório local.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-139">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="eb4c3-140">A execução da ferramenta com a opção **/roaming** se aplica a todas as ações no repositório compatível com roaming.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-140">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="eb4c3-141">A execução da ferramenta com a opção **/machine** se aplica a todas as ações no repositório do computador.</span><span class="sxs-lookup"><span data-stu-id="eb4c3-141">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb4c3-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb4c3-142">See also</span></span>

- [<span data-ttu-id="eb4c3-143">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="eb4c3-143">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="eb4c3-144">Armazenamentos isolado</span><span class="sxs-lookup"><span data-stu-id="eb4c3-144">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
- [<span data-ttu-id="eb4c3-145">Prompts de comando</span><span class="sxs-lookup"><span data-stu-id="eb4c3-145">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
