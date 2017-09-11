---
title: /subsystemversion (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: efeade3fcde18f02b3a760adc50d3555df6c9ed7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="subsystemversion-visual-basic"></a><span data-ttu-id="303e0-102">/subsystemversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="303e0-102">/subsystemversion (Visual Basic)</span></span>
<span data-ttu-id="303e0-103">Especifica a versão mínima do subsistema no qual pode executar o arquivo executável gerado, assim, determinar as versões do Windows no qual o arquivo executável pode executar.</span><span class="sxs-lookup"><span data-stu-id="303e0-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="303e0-104">Normalmente, essa opção garante que o arquivo executável pode aproveitar os recursos de segurança em especial que não estão disponíveis com versões anteriores do Windows.</span><span class="sxs-lookup"><span data-stu-id="303e0-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="303e0-105">Para especificar o próprio subsistema, use o [/destino](../../../csharp/language-reference/compiler-options/target-compiler-option.md) opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="303e0-105">To specify the subsystem itself, use the [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="303e0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="303e0-106">Syntax</span></span>  
  
```vb  
/subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a><span data-ttu-id="303e0-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="303e0-107">Parameters</span></span>  
 `major.minor`  
 <span data-ttu-id="303e0-108">A versão mínima necessária do subsistema, conforme expresso em uma notação de ponto para versões principais e secundárias.</span><span class="sxs-lookup"><span data-stu-id="303e0-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="303e0-109">Por exemplo, você pode especificar que um aplicativo não pode ser executado em um sistema operacional que é mais antigo que o Windows 7 se você definir o valor dessa opção como 6.01, conforme descrito na tabela mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="303e0-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="303e0-110">Você deve especificar os valores de `major` e `minor` como inteiros.</span><span class="sxs-lookup"><span data-stu-id="303e0-110">You must specify the values for `major` and `minor` as integers.</span></span>  
  
 <span data-ttu-id="303e0-111">Zeros à esquerda `minor` versão não altera a versão, mas fazer zeros à direita.</span><span class="sxs-lookup"><span data-stu-id="303e0-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="303e0-112">Por exemplo, 6.1 e 6.01 referem-se a mesma versão, mas 6.10 refere-se a uma versão diferente.</span><span class="sxs-lookup"><span data-stu-id="303e0-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="303e0-113">É recomendável expressar a versão secundária como dois dígitos para evitar confusão.</span><span class="sxs-lookup"><span data-stu-id="303e0-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="303e0-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="303e0-114">Remarks</span></span>  
 <span data-ttu-id="303e0-115">A seguinte tabela lista as versões do subsistema comuns do Windows.</span><span class="sxs-lookup"><span data-stu-id="303e0-115">The following table lists common subsystem versions of Windows.</span></span>  
  
|<span data-ttu-id="303e0-116">Versão do Windows</span><span class="sxs-lookup"><span data-stu-id="303e0-116">Windows version</span></span>|<span data-ttu-id="303e0-117">Versão do subsistema</span><span class="sxs-lookup"><span data-stu-id="303e0-117">Subsystem version</span></span>|  
|---------------------|-----------------------|  
|<span data-ttu-id="303e0-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="303e0-118">Windows 2000</span></span>|<span data-ttu-id="303e0-119">5.00</span><span class="sxs-lookup"><span data-stu-id="303e0-119">5.00</span></span>|  
|<span data-ttu-id="303e0-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="303e0-120">Windows XP</span></span>|<span data-ttu-id="303e0-121">5.01</span><span class="sxs-lookup"><span data-stu-id="303e0-121">5.01</span></span>|  
|<span data-ttu-id="303e0-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="303e0-122">Windows Server 2003</span></span>|<span data-ttu-id="303e0-123">5.02</span><span class="sxs-lookup"><span data-stu-id="303e0-123">5.02</span></span>|  
|<span data-ttu-id="303e0-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="303e0-124">Windows Vista</span></span>|<span data-ttu-id="303e0-125">6.00</span><span class="sxs-lookup"><span data-stu-id="303e0-125">6.00</span></span>|  
|<span data-ttu-id="303e0-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="303e0-126">Windows 7</span></span>|<span data-ttu-id="303e0-127">6.01</span><span class="sxs-lookup"><span data-stu-id="303e0-127">6.01</span></span>|  
|<span data-ttu-id="303e0-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="303e0-128">Windows Server 2008</span></span>|<span data-ttu-id="303e0-129">6.01</span><span class="sxs-lookup"><span data-stu-id="303e0-129">6.01</span></span>|  
|[!INCLUDE[win8](../../../csharp/language-reference/compiler-options/includes/win8_md.md)]|<span data-ttu-id="303e0-130">6.02</span><span class="sxs-lookup"><span data-stu-id="303e0-130">6.02</span></span>|  
  
## <a name="default-values"></a><span data-ttu-id="303e0-131">Valores padrão</span><span class="sxs-lookup"><span data-stu-id="303e0-131">Default values</span></span>  
 <span data-ttu-id="303e0-132">O valor padrão de **/subsystemversion** opção de compilador depende das condições na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="303e0-132">The default value of the **/subsystemversion** compiler option depends on the conditions in the following list:</span></span>  
  
-   <span data-ttu-id="303e0-133">O valor padrão é 6.02 se qualquer opção de compilador na lista a seguir é definida:</span><span class="sxs-lookup"><span data-stu-id="303e0-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>  
  
    -   [<span data-ttu-id="303e0-134">/target: appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="303e0-134">/target:appcontainerexe</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [<span data-ttu-id="303e0-135">/target: winmdobj</span><span class="sxs-lookup"><span data-stu-id="303e0-135">/target:winmdobj</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [<span data-ttu-id="303e0-136">/Platform:ARM</span><span class="sxs-lookup"><span data-stu-id="303e0-136">/platform:arm</span></span>](../../../visual-basic/reference/command-line-compiler/platform.md)  
  
-   <span data-ttu-id="303e0-137">O valor padrão é 6.00 se você estiver usando o MSBuild, você deseja [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net_v45_md.md)], e você não definir qualquer uma das opções de compilador que foram especificadas anteriormente na lista.</span><span class="sxs-lookup"><span data-stu-id="303e0-137">The default value is 6.00 if you're using MSBuild, you're targeting [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net_v45_md.md)], and you haven't set any of the compiler options that were specified earlier in this list.</span></span>  
  
-   <span data-ttu-id="303e0-138">O valor padrão é 4.00 se nenhuma das condições anteriores for true.</span><span class="sxs-lookup"><span data-stu-id="303e0-138">The default value is 4.00 if none of the previous conditions is true.</span></span>  
  
## <a name="setting-this-option"></a><span data-ttu-id="303e0-139">Definindo esta opção</span><span class="sxs-lookup"><span data-stu-id="303e0-139">Setting this option</span></span>  
 <span data-ttu-id="303e0-140">Para definir o **/subsystemversion** opção de compilador no Visual Studio, abra o arquivo. vbproj e especifique um valor para o `SubsystemVersion` propriedade no XML MSBuild.</span><span class="sxs-lookup"><span data-stu-id="303e0-140">To set the **/subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="303e0-141">Você não pode definir essa opção no IDE do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="303e0-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="303e0-142">Para obter mais informações, consulte "Valores padrão" anteriormente neste tópico ou [propriedades comuns de projeto MSBuild](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="303e0-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="303e0-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="303e0-143">See Also</span></span>  
[<span data-ttu-id="303e0-144">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="303e0-144">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

[<span data-ttu-id="303e0-145">Propriedades MSBuild</span><span class="sxs-lookup"><span data-stu-id="303e0-145">MSBuild Properties</span></span>](https://docs.microsoft.com/visualstudio/msbuild/msbuild-properties)

