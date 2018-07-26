---
title: -subsystemversion (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22eb8aa1cd86dba4a1a65edf31a3b18df7085a33
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245457"
---
# <a name="-subsystemversion-visual-basic"></a><span data-ttu-id="856f5-102">-subsystemversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="856f5-102">-subsystemversion (Visual Basic)</span></span>
<span data-ttu-id="856f5-103">Especifica a versão mínima do subsistema no qual o arquivo executável gerado pode ser executado, determinando assim as versões do Windows em que o arquivo executável pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="856f5-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="856f5-104">Normalmente, essa opção garante que o arquivo executável possa tirar proveito de determinados recursos de segurança que não estão disponíveis com versões mais antigas do Windows.</span><span class="sxs-lookup"><span data-stu-id="856f5-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="856f5-105">Para especificar o subsistema em si, use a opção do compilador [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="856f5-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="856f5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="856f5-106">Syntax</span></span>  
  
```vb  
-subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a><span data-ttu-id="856f5-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="856f5-107">Parameters</span></span>  
 `major.minor`  
 <span data-ttu-id="856f5-108">A versão mínima obrigatória do subsistema, conforme expresso em uma notação de ponto para versões principais e secundárias.</span><span class="sxs-lookup"><span data-stu-id="856f5-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="856f5-109">Por exemplo, você pode especificar que um aplicativo não pode ser executado em um sistema operacional mais antigo que o Windows 7 se definir o valor dessa opção como 6.01, conforme descrito na tabela mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="856f5-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="856f5-110">Você deve especificar os valores de `major` e `minor` como inteiros.</span><span class="sxs-lookup"><span data-stu-id="856f5-110">You must specify the values for `major` and `minor` as integers.</span></span>  
  
 <span data-ttu-id="856f5-111">Zeros à esquerda na versão `minor` não alteram a versão, mas zeros à direita alteram.</span><span class="sxs-lookup"><span data-stu-id="856f5-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="856f5-112">Por exemplo, 6.1 e 6.01 se referem à mesma versão, mas 6.10 se refere a uma versão diferente.</span><span class="sxs-lookup"><span data-stu-id="856f5-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="856f5-113">É recomendável expressar a versão secundária como dois dígitos para evitar confusão.</span><span class="sxs-lookup"><span data-stu-id="856f5-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="856f5-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="856f5-114">Remarks</span></span>  
 <span data-ttu-id="856f5-115">A seguinte tabela lista as versões de subsistema comuns do Windows.</span><span class="sxs-lookup"><span data-stu-id="856f5-115">The following table lists common subsystem versions of Windows.</span></span>  
  
|<span data-ttu-id="856f5-116">Versão do Windows</span><span class="sxs-lookup"><span data-stu-id="856f5-116">Windows version</span></span>|<span data-ttu-id="856f5-117">Versão do subsistema</span><span class="sxs-lookup"><span data-stu-id="856f5-117">Subsystem version</span></span>|  
|---------------------|-----------------------|  
|<span data-ttu-id="856f5-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="856f5-118">Windows 2000</span></span>|<span data-ttu-id="856f5-119">5.00</span><span class="sxs-lookup"><span data-stu-id="856f5-119">5.00</span></span>|  
|<span data-ttu-id="856f5-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="856f5-120">Windows XP</span></span>|<span data-ttu-id="856f5-121">5.01</span><span class="sxs-lookup"><span data-stu-id="856f5-121">5.01</span></span>|  
|<span data-ttu-id="856f5-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="856f5-122">Windows Server 2003</span></span>|<span data-ttu-id="856f5-123">5.02</span><span class="sxs-lookup"><span data-stu-id="856f5-123">5.02</span></span>|  
|<span data-ttu-id="856f5-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="856f5-124">Windows Vista</span></span>|<span data-ttu-id="856f5-125">6.00</span><span class="sxs-lookup"><span data-stu-id="856f5-125">6.00</span></span>|  
|<span data-ttu-id="856f5-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="856f5-126">Windows 7</span></span>|<span data-ttu-id="856f5-127">6.01</span><span class="sxs-lookup"><span data-stu-id="856f5-127">6.01</span></span>|  
|<span data-ttu-id="856f5-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="856f5-128">Windows Server 2008</span></span>|<span data-ttu-id="856f5-129">6.01</span><span class="sxs-lookup"><span data-stu-id="856f5-129">6.01</span></span>|  
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="856f5-130">6.02</span><span class="sxs-lookup"><span data-stu-id="856f5-130">6.02</span></span>|  
  
## <a name="default-values"></a><span data-ttu-id="856f5-131">Valores padrão</span><span class="sxs-lookup"><span data-stu-id="856f5-131">Default values</span></span>  
 <span data-ttu-id="856f5-132">O valor padrão da opção do compilador **-subsystemversion** depende das condições na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="856f5-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>  
  
-   <span data-ttu-id="856f5-133">O valor padrão é 6.02 se qualquer opção do compilador na lista a seguir for definida:</span><span class="sxs-lookup"><span data-stu-id="856f5-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>  
  
    -   [<span data-ttu-id="856f5-134">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="856f5-134">-target:appcontainerexe</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [<span data-ttu-id="856f5-135">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="856f5-135">-target:winmdobj</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [<span data-ttu-id="856f5-136">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="856f5-136">-platform:arm</span></span>](../../../visual-basic/reference/command-line-compiler/platform.md)  
  
-   <span data-ttu-id="856f5-137">O valor padrão é 6.00 se você estiver usando o MSBuild, se tiver como alvo [!INCLUDE[net_v45](~/includes/net-v45-md.md)] e se não tiver definido nenhuma das opções de compilador que foram especificadas anteriormente na lista.</span><span class="sxs-lookup"><span data-stu-id="856f5-137">The default value is 6.00 if you're using MSBuild, you're targeting [!INCLUDE[net_v45](~/includes/net-v45-md.md)], and you haven't set any of the compiler options that were specified earlier in this list.</span></span>  
  
-   <span data-ttu-id="856f5-138">O valor padrão é 4.00 se nenhuma das condições anteriores for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="856f5-138">The default value is 4.00 if none of the previous conditions is true.</span></span>  
  
## <a name="setting-this-option"></a><span data-ttu-id="856f5-139">Definindo esta opção</span><span class="sxs-lookup"><span data-stu-id="856f5-139">Setting this option</span></span>  
 <span data-ttu-id="856f5-140">Para definir a **- subsystemversion** opção de compilador no Visual Studio, abra o arquivo. vbproj e especifique um valor para o `SubsystemVersion` propriedade no XML do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="856f5-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="856f5-141">Você não pode definir essa opção no IDE do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="856f5-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="856f5-142">Para obter mais informações, consulte "Valores padrão" no início deste tópico ou [Propriedades de projeto comuns do MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="856f5-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="856f5-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="856f5-143">See Also</span></span>  
[<span data-ttu-id="856f5-144">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="856f5-144">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

[<span data-ttu-id="856f5-145">Propriedades MSBuild</span><span class="sxs-lookup"><span data-stu-id="856f5-145">MSBuild Properties</span></span>](/visualstudio/msbuild/msbuild-properties)
