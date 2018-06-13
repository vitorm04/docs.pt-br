---
title: Clrver.exe (Ferramenta de Versão do CLR)
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 998ebb76b536b04d617bafdb74a3014c68cf509d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405558"
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="52d41-102">Clrver.exe (Ferramenta de Versão do CLR)</span><span class="sxs-lookup"><span data-stu-id="52d41-102">Clrver.exe (CLR Version Tool)</span></span>
<span data-ttu-id="52d41-103">A ferramenta Versão do CLR (Clrver.exe) relata todas as versões instaladas do CLR (Common Language Runtime) no computador.</span><span class="sxs-lookup"><span data-stu-id="52d41-103">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="52d41-104">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="52d41-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="52d41-105">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="52d41-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="52d41-106">Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="52d41-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="52d41-107">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="52d41-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52d41-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52d41-108">Syntax</span></span>  
  
```  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="52d41-109">Opções</span><span class="sxs-lookup"><span data-stu-id="52d41-109">Options</span></span>  
  
|<span data-ttu-id="52d41-110">Opção</span><span class="sxs-lookup"><span data-stu-id="52d41-110">Option</span></span>|<span data-ttu-id="52d41-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="52d41-111">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="52d41-112">Exibe todos os processos no computador que estão usando o CLR.</span><span class="sxs-lookup"><span data-stu-id="52d41-112">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="52d41-113">*pid*</span><span class="sxs-lookup"><span data-stu-id="52d41-113">*pid*</span></span>|<span data-ttu-id="52d41-114">Exibe as versões do CLR usado pelo processo com a PID (ID de processo especificado).</span><span class="sxs-lookup"><span data-stu-id="52d41-114">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="52d41-115">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="52d41-115">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52d41-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="52d41-116">Remarks</span></span>  
 <span data-ttu-id="52d41-117">Se você chamar Clrver.exe sem opções, ele exibirá todas as versões do CLR instaladas.</span><span class="sxs-lookup"><span data-stu-id="52d41-117">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="52d41-118">Se especificar uma PID para outro usuário, você deverá ter permissões administrativas para obter as informações da versão.</span><span class="sxs-lookup"><span data-stu-id="52d41-118">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52d41-119">No Windows Vista e posterior, UAC (Controle de Conta de Usuário) determina os privilégios de um usuário.</span><span class="sxs-lookup"><span data-stu-id="52d41-119">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="52d41-120">Se for um membro do grupo Administradores Internos, você receberá dois tokens de acesso do tempo de execução: um token de acesso do usuário padrão e um token de acesso do administrador.</span><span class="sxs-lookup"><span data-stu-id="52d41-120">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="52d41-121">Por padrão, você está na função de usuário padrão.</span><span class="sxs-lookup"><span data-stu-id="52d41-121">By default, you are in the standard user role.</span></span> <span data-ttu-id="52d41-122">Para executar o código que exige a permissão administrativa, você deve primeiro elevar os privilégios do usuário padrão para o administrador.</span><span class="sxs-lookup"><span data-stu-id="52d41-122">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="52d41-123">Você pode fazer isso ao iniciar o prompt de comando clicando com o botão direito do mouse no ícone do prompt de comando e indicando que você deseja executar como administrador.</span><span class="sxs-lookup"><span data-stu-id="52d41-123">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="52d41-124">A tentativa de determinar a versão do CLR dos processos SYSTEM, LOCAL SERVICE e NETWORK SERVICE resulta em uma mensagem indicando que a PID não existe.</span><span class="sxs-lookup"><span data-stu-id="52d41-124">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="52d41-125">Exemplos</span><span class="sxs-lookup"><span data-stu-id="52d41-125">Examples</span></span>  
 <span data-ttu-id="52d41-126">O comando a seguir exibe todas as versões do CLR instaladas no computador.</span><span class="sxs-lookup"><span data-stu-id="52d41-126">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="52d41-127">O comando a seguir exibe a versão do CLR usada pelo processo 128.</span><span class="sxs-lookup"><span data-stu-id="52d41-127">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="52d41-128">O comando a seguir exibe todos os processos gerenciados e a versão do CLR que eles estão usando.</span><span class="sxs-lookup"><span data-stu-id="52d41-128">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="52d41-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52d41-129">See Also</span></span>  
 [<span data-ttu-id="52d41-130">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="52d41-130">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="52d41-131">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="52d41-131">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
