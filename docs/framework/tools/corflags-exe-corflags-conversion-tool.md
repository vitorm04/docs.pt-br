---
title: CorFlags.exe (Ferramenta de Conversão de CorFlags)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63e70ae8cd110786ad7d2069088dbfdfde736a28
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846740"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="4d1d6-102">CorFlags.exe (Ferramenta de Conversão de CorFlags)</span><span class="sxs-lookup"><span data-stu-id="4d1d6-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="4d1d6-103">A ferramenta Conversão CorFlags permite configurar a seção CorFlags do cabeçalho de uma imagem PE (Portable Executable).</span><span class="sxs-lookup"><span data-stu-id="4d1d6-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="4d1d6-104">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="4d1d6-105">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="4d1d6-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="4d1d6-106">Para obter mais informações, consulte [Prompts de Comando](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="4d1d6-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="4d1d6-107">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4d1d6-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d1d6-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d1d6-108">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d1d6-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4d1d6-109">Parameters</span></span>  
  
|<span data-ttu-id="4d1d6-110">Parâmetro obrigatório</span><span class="sxs-lookup"><span data-stu-id="4d1d6-110">Required parameter</span></span>|<span data-ttu-id="4d1d6-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d1d6-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="4d1d6-112">O nome do assembly para o qual configurar o CorFlags.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="4d1d6-113">Opção</span><span class="sxs-lookup"><span data-stu-id="4d1d6-113">Option</span></span>|<span data-ttu-id="4d1d6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d1d6-114">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="4d1d6-115">Define o sinalizador 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-115">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="4d1d6-116">Limpa o sinalizador 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-116">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="4d1d6-117">Define o sinalizador 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-117">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="4d1d6-118">O aplicativo é executado como um processo 32 bits, mesmo em plataformas 64 bits.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-118">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="4d1d6-119">Defina esse sinalizador apenas em arquivos EXE.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-119">Set this flag only on EXE files.</span></span> <span data-ttu-id="4d1d6-120">Se o sinalizador for definido em uma DLL, a DLL não será carregada em processos 64 bits, e uma exceção <xref:System.BadImageFormatException> será acionada.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-120">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="4d1d6-121">Um arquivo EXE com esse sinalizador pode ser carregado em um processo 64 bits.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-121">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="4d1d6-122">Novidades no .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-122">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="4d1d6-123">Limpa o sinalizador 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-123">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="4d1d6-124">Novidades no .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-124">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="4d1d6-125">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-125">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="4d1d6-126">Força uma atualização, mesmo que o assembly tenha nome forte.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-126">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="4d1d6-127">**Importante:** se atualizar um assembly de nome forte, você deverá assiná-lo novamente antes de executar o código.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-127">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="4d1d6-128">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-128">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="4d1d6-129">Define o sinalizador ILONLY.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-129">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="4d1d6-130">Limpa o sinalizador ILONLY.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-130">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="4d1d6-131">Suprime a exibição do banner de inicialização da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-131">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="4d1d6-132">Reverte a versão do cabeçalho do CLR para 2.0.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-132">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="4d1d6-133">Atualiza a versão do cabeçalho do CLR para 2.5.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-133">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="4d1d6-134">**Observação:** os assemblies devem ter uma versão do cabeçalho do CLR 2.5 ou posterior para serem executados nativamente.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-134">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d1d6-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d1d6-135">Remarks</span></span>  
 <span data-ttu-id="4d1d6-136">Se nenhuma opção estiver especificada, a ferramenta Conversão CorFlags exibirá os sinalizadores para o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="4d1d6-136">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d1d6-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d1d6-137">See also</span></span>

- [<span data-ttu-id="4d1d6-138">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="4d1d6-138">Tools</span></span>](index.md)
- [<span data-ttu-id="4d1d6-139">Aplicativos de 64 bits</span><span class="sxs-lookup"><span data-stu-id="4d1d6-139">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="4d1d6-140">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="4d1d6-140">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
