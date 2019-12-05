---
title: -subsystemversion (opções do compilador C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: d76c9424340b4b6f3c211c849b466be55eb79d1e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802039"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="49e7c-102">-subsystemversion (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="49e7c-102">-subsystemversion (C# Compiler Options)</span></span>

<span data-ttu-id="49e7c-103">Especifica a versão mínima do subsistema no qual o arquivo executável gerado pode ser executado, determinando assim as versões do Windows em que o arquivo executável pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="49e7c-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="49e7c-104">Normalmente, essa opção garante que o arquivo executável possa tirar proveito de determinados recursos de segurança que não estão disponíveis com versões mais antigas do Windows.</span><span class="sxs-lookup"><span data-stu-id="49e7c-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="49e7c-105">Para especificar o subsistema em si, use a opção do compilador [-target](./target-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="49e7c-105">To specify the subsystem itself, use the [-target](./target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="49e7c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49e7c-106">Syntax</span></span>

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="49e7c-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49e7c-107">Parameters</span></span>

`major.minor`

<span data-ttu-id="49e7c-108">A versão mínima obrigatória do subsistema, conforme expresso em uma notação de ponto para versões principais e secundárias.</span><span class="sxs-lookup"><span data-stu-id="49e7c-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="49e7c-109">Por exemplo, você pode especificar que um aplicativo não pode ser executado em um sistema operacional mais antigo que o Windows 7 se definir o valor dessa opção como 6.01, conforme descrito na tabela mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="49e7c-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="49e7c-110">Você deve especificar os valores de `major` e `minor` como inteiros.</span><span class="sxs-lookup"><span data-stu-id="49e7c-110">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="49e7c-111">Zeros à esquerda na versão `minor` não alteram a versão, mas zeros à direita alteram.</span><span class="sxs-lookup"><span data-stu-id="49e7c-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="49e7c-112">Por exemplo, 6.1 e 6.01 se referem à mesma versão, mas 6.10 se refere a uma versão diferente.</span><span class="sxs-lookup"><span data-stu-id="49e7c-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="49e7c-113">É recomendável expressar a versão secundária como dois dígitos para evitar confusão.</span><span class="sxs-lookup"><span data-stu-id="49e7c-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="49e7c-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="49e7c-114">Remarks</span></span>

<span data-ttu-id="49e7c-115">A seguinte tabela lista as versões de subsistema comuns do Windows.</span><span class="sxs-lookup"><span data-stu-id="49e7c-115">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="49e7c-116">Versão do Windows</span><span class="sxs-lookup"><span data-stu-id="49e7c-116">Windows version</span></span>|<span data-ttu-id="49e7c-117">Versão do subsistema</span><span class="sxs-lookup"><span data-stu-id="49e7c-117">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="49e7c-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="49e7c-118">Windows 2000</span></span>|<span data-ttu-id="49e7c-119">5.00</span><span class="sxs-lookup"><span data-stu-id="49e7c-119">5.00</span></span>|
|<span data-ttu-id="49e7c-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="49e7c-120">Windows XP</span></span>|<span data-ttu-id="49e7c-121">5.01</span><span class="sxs-lookup"><span data-stu-id="49e7c-121">5.01</span></span>|
|<span data-ttu-id="49e7c-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="49e7c-122">Windows Server 2003</span></span>|<span data-ttu-id="49e7c-123">5.02</span><span class="sxs-lookup"><span data-stu-id="49e7c-123">5.02</span></span>|
|<span data-ttu-id="49e7c-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="49e7c-124">Windows Vista</span></span>|<span data-ttu-id="49e7c-125">6.00</span><span class="sxs-lookup"><span data-stu-id="49e7c-125">6.00</span></span>|
|<span data-ttu-id="49e7c-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="49e7c-126">Windows 7</span></span>|<span data-ttu-id="49e7c-127">6.01</span><span class="sxs-lookup"><span data-stu-id="49e7c-127">6.01</span></span>|
|<span data-ttu-id="49e7c-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="49e7c-128">Windows Server 2008</span></span>|<span data-ttu-id="49e7c-129">6.01</span><span class="sxs-lookup"><span data-stu-id="49e7c-129">6.01</span></span>|
|<span data-ttu-id="49e7c-130">Windows 8</span><span class="sxs-lookup"><span data-stu-id="49e7c-130">Windows 8</span></span>|<span data-ttu-id="49e7c-131">6.02</span><span class="sxs-lookup"><span data-stu-id="49e7c-131">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="49e7c-132">Valores padrão</span><span class="sxs-lookup"><span data-stu-id="49e7c-132">Default values</span></span>

<span data-ttu-id="49e7c-133">O valor padrão da opção do compilador **-subsystemversion** depende das condições na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="49e7c-133">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="49e7c-134">O valor padrão é 6.02 se qualquer opção do compilador na lista a seguir for definida:</span><span class="sxs-lookup"><span data-stu-id="49e7c-134">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="49e7c-135">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="49e7c-135">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)

  - [<span data-ttu-id="49e7c-136">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="49e7c-136">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)

  - [<span data-ttu-id="49e7c-137">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="49e7c-137">-platform:arm</span></span>](./platform-compiler-option.md)

- <span data-ttu-id="49e7c-138">O valor padrão será 6.00 se você estiver usando o MSBuild, se tiver como destino o .NET Framework 4.5 e se não definiu nenhuma das opções de compilador que foram especificadas anteriormente na lista.</span><span class="sxs-lookup"><span data-stu-id="49e7c-138">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="49e7c-139">O valor padrão é 4.00 se nenhuma das condições anteriores for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="49e7c-139">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="49e7c-140">Definindo esta opção</span><span class="sxs-lookup"><span data-stu-id="49e7c-140">Setting this option</span></span>

<span data-ttu-id="49e7c-141">Para definir a opção do compilador **-subsystemversion** no Visual Studio, você precisa abrir o arquivo .csproj e especificar um valor para a propriedade `SubsystemVersion` no XML do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="49e7c-141">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="49e7c-142">Você não pode definir essa opção no IDE do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49e7c-142">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="49e7c-143">Para obter mais informações, consulte "Valores padrão" no início deste tópico ou [Propriedades de projeto comuns do MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="49e7c-143">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="49e7c-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49e7c-144">See also</span></span>

- [<span data-ttu-id="49e7c-145">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="49e7c-145">C# Compiler Options</span></span>](./index.md)
