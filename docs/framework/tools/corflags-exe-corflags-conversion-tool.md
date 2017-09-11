---
title: "CorFlags.exe (Ferramenta de Conversão de CorFlags)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
caps.latest.revision: 17
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 80fb48fc86d3010020a0a8a79bb2b4b7a6275368
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="00a08-102">CorFlags.exe (Ferramenta de Conversão de CorFlags)</span><span class="sxs-lookup"><span data-stu-id="00a08-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="00a08-103">A ferramenta Conversão CorFlags permite configurar a seção CorFlags do cabeçalho de uma imagem PE (Portable Executable).</span><span class="sxs-lookup"><span data-stu-id="00a08-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="00a08-104">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="00a08-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="00a08-105">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="00a08-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="00a08-106">Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="00a08-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="00a08-107">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="00a08-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00a08-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00a08-108">Syntax</span></span>  
  
```  
CorFlags.exe assembly [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00a08-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="00a08-109">Parameters</span></span>  
  
|<span data-ttu-id="00a08-110">Parâmetro obrigatório</span><span class="sxs-lookup"><span data-stu-id="00a08-110">Required parameter</span></span>|<span data-ttu-id="00a08-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="00a08-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="00a08-112">O nome do assembly para o qual configurar o CorFlags.</span><span class="sxs-lookup"><span data-stu-id="00a08-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="00a08-113">Opção</span><span class="sxs-lookup"><span data-stu-id="00a08-113">Option</span></span>|<span data-ttu-id="00a08-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="00a08-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="00a08-115">**/32BIT[REQ]+**</span><span class="sxs-lookup"><span data-stu-id="00a08-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="00a08-116">Define o sinalizador 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="00a08-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="00a08-117">**/32BIT[REQ]-**</span><span class="sxs-lookup"><span data-stu-id="00a08-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="00a08-118">Limpa o sinalizador 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="00a08-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="00a08-119">**/32BITPREF+**</span><span class="sxs-lookup"><span data-stu-id="00a08-119">**/32BITPREF+**</span></span>|<span data-ttu-id="00a08-120">Define o sinalizador 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="00a08-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="00a08-121">O aplicativo é executado como um processo 32 bits, mesmo em plataformas 64 bits.</span><span class="sxs-lookup"><span data-stu-id="00a08-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="00a08-122">Defina esse sinalizador apenas em arquivos EXE.</span><span class="sxs-lookup"><span data-stu-id="00a08-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="00a08-123">Se o sinalizador for definido em uma DLL, a DLL não será carregada em processos 64 bits, e uma exceção <xref:System.BadImageFormatException> será acionada.</span><span class="sxs-lookup"><span data-stu-id="00a08-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="00a08-124">Um arquivo EXE com esse sinalizador pode ser carregado em um processo 64 bits.</span><span class="sxs-lookup"><span data-stu-id="00a08-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="00a08-125">Novidades no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="00a08-125">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="00a08-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="00a08-126">**/32BITPREF-**</span></span>|<span data-ttu-id="00a08-127">Limpa o sinalizador 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="00a08-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="00a08-128">Novidades no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="00a08-128">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="00a08-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="00a08-129">**/?**</span></span>|<span data-ttu-id="00a08-130">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="00a08-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="00a08-131">**/Force**</span><span class="sxs-lookup"><span data-stu-id="00a08-131">**/Force**</span></span>|<span data-ttu-id="00a08-132">Força uma atualização, mesmo que o assembly tenha nome forte.</span><span class="sxs-lookup"><span data-stu-id="00a08-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="00a08-133">**Importante:** se atualizar um assembly de nome forte, você deverá assiná-lo novamente antes de executar o código.</span><span class="sxs-lookup"><span data-stu-id="00a08-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="00a08-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="00a08-134">**/help**</span></span>|<span data-ttu-id="00a08-135">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="00a08-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="00a08-136">**/ILONLY+**</span><span class="sxs-lookup"><span data-stu-id="00a08-136">**/ILONLY+**</span></span>|<span data-ttu-id="00a08-137">Define o sinalizador ILONLY.</span><span class="sxs-lookup"><span data-stu-id="00a08-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="00a08-138">**/ILONLY-**</span><span class="sxs-lookup"><span data-stu-id="00a08-138">**/ILONLY-**</span></span>|<span data-ttu-id="00a08-139">Limpa o sinalizador ILONLY.</span><span class="sxs-lookup"><span data-stu-id="00a08-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="00a08-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="00a08-140">**/nologo**</span></span>|<span data-ttu-id="00a08-141">Suprime a exibição do banner de inicialização da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="00a08-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="00a08-142">**/RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="00a08-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="00a08-143">Reverte a versão do cabeçalho do CLR para 2.0.</span><span class="sxs-lookup"><span data-stu-id="00a08-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="00a08-144">**/UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="00a08-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="00a08-145">Atualiza a versão do cabeçalho do CLR para 2.5.</span><span class="sxs-lookup"><span data-stu-id="00a08-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="00a08-146">**Observação:** os assemblies devem ter uma versão do cabeçalho do CLR 2.5 ou posterior para serem executados nativamente.</span><span class="sxs-lookup"><span data-stu-id="00a08-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00a08-147">Comentários</span><span class="sxs-lookup"><span data-stu-id="00a08-147">Remarks</span></span>  
 <span data-ttu-id="00a08-148">Se nenhuma opção estiver especificada, a ferramenta Conversão CorFlags exibirá os sinalizadores para o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="00a08-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a08-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00a08-149">See Also</span></span>  
 <span data-ttu-id="00a08-150">[Ferramentas](../../../docs/framework/tools/index.md) </span><span class="sxs-lookup"><span data-stu-id="00a08-150">[Tools](../../../docs/framework/tools/index.md) </span></span>  
 <span data-ttu-id="00a08-151">[Aplicativos de 64 bits](../../../docs/framework/64-bit-apps.md) </span><span class="sxs-lookup"><span data-stu-id="00a08-151">[64-bit Applications](../../../docs/framework/64-bit-apps.md) </span></span>  
 [<span data-ttu-id="00a08-152">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="00a08-152">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

