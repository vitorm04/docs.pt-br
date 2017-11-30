---
title: Direcionando o .NET Framework 2.0 no Windows 8
description: "Saiba mais sobre direcionando a versão mais antiga do .NET Framework ao usar o F #."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63989543-95c3-4ab7-81f3-3834a8b15010
ms.openlocfilehash: 2c0191267da5bee7b844c11cdee168ccfb3321c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="targeting-older-versions-of-net"></a><span data-ttu-id="d5ac8-104">Direcionamento de versões mais antigas do .NET</span><span class="sxs-lookup"><span data-stu-id="d5ac8-104">Targeting Older Versions of .NET</span></span>

> [!NOTE]
<span data-ttu-id="d5ac8-105">Este artigo não é atualizado com o mais recente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-105">This article is not up to date with the latest Visual Studio.</span></span>  <span data-ttu-id="d5ac8-106">Ele será atualizado.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-106">It will be updated.</span></span>

<span data-ttu-id="d5ac8-107">O seguinte erro pode aparecer se você tentar direcionar o .NET Framework 2.0, 3.0 ou 3.5 em F # projeto quando o Visual Studio está instalado no Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="d5ac8-107">The following error might appear if you try to target the .NET Framework 2.0, 3.0, or 3.5 in an F# project when Visual Studio is installed on Windows 8.1:</span></span> 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

<span data-ttu-id="d5ac8-108">Esse erro costuma ocorrer sob a seguinte combinação de condições:</span><span class="sxs-lookup"><span data-stu-id="d5ac8-108">This error is known to occur under the following combination of conditions:</span></span>


- <span data-ttu-id="d5ac8-109">Você instalou o Visual Studio Windows 8.1.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-109">You installed Visual Studio on Windows 8.1.</span></span>
<br />

- <span data-ttu-id="d5ac8-110">Você não habilitar o .NET Framework 3.5 antes de instalar o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-110">You didn’t enable the .NET Framework 3.5 before you installed Visual Studio.</span></span>
<br />

- <span data-ttu-id="d5ac8-111">Seu projeto direcionado ao .NET Framework 2.0, 3.0 ou 3.5.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-111">Your project targets the .NET Framework 2.0, 3.0, or 3.5.</span></span>
<br />

<span data-ttu-id="d5ac8-112">Quando você instala o Visual Studio, ele detecta as versões instaladas do .NET Framework e instala o tempo de execução 2.0 F # somente se o .NET Framework 3.5 está instalado e habilitado.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-112">When you install Visual Studio, it detects the installed versions of the .NET Framework and installs the F# 2.0 Runtime only if the .NET Framework 3.5 is installed and enabled.</span></span>


## <a name="resolving-the-error"></a><span data-ttu-id="d5ac8-113">Resolver o erro</span><span class="sxs-lookup"><span data-stu-id="d5ac8-113">Resolving the Error</span></span>
<span data-ttu-id="d5ac8-114">Para resolver esse erro, você pode ou uma versão mais recente do .NET Framework de destino, ou você pode habilitar o .NET Framework 3.5 no Windows 8.1 e, em seguida, instalar o runtime do F # 2.0 executando o programa de instalação do Visual Studio com o **reparo** opção.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-114">To resolve this error, you can either target a newer version of the .NET Framework, or you can enable the .NET Framework 3.5 on Windows 8.1 and then install the F# 2.0 runtime by running the setup program for Visual Studio with the **Repair** option.</span></span>


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a><span data-ttu-id="d5ac8-115">Para habilitar o .NET Framework 3.5 no Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d5ac8-115">To enable the .NET Framework 3.5 on Windows 8.1</span></span>

1. <span data-ttu-id="d5ac8-116">Sobre o **iniciar** tela, comece a digitar **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-116">On the **Start** screen, start to enter **Control Panel**.</span></span>
<br />  <span data-ttu-id="d5ac8-117">Quando você insere esse nome, o **painel de controle** aparece sob o **aplicativos** título.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-117">As you enter that name, the **Control Panel** icon appears under the **Apps** heading.</span></span>
<br />

2. <span data-ttu-id="d5ac8-118">Escolha o **painel de controle** ícone, escolha o **programas** ícone e, em seguida, escolha o **ativar recursos do Windows ou desativar** link.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-118">Choose the **Control Panel** icon, choose the **Programs** icon, and then choose the **Turn Windows features on or off** link.</span></span>
<br />

3. <span data-ttu-id="d5ac8-119">Verifique se o **.NET Framework 3.5 (inclui .NET 2.0 e 3.0)** caixa de seleção está selecionada e, em seguida, escolha o **Okey** botão.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-119">Make sure that the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box is selected, and then choose the **OK** button.</span></span>
<br />  <span data-ttu-id="d5ac8-120">Você não precisa selecionar as caixas de seleção para todos os nós filho para os componentes opcionais do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-120">You don’t need to select the check boxes for any child nodes for optional components of the .NET Framework.</span></span>
<br />  <span data-ttu-id="d5ac8-121">O .NET Framework 3.5 está habilitada, se já não.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-121">The .NET Framework 3.5 is enabled if it wasn't already.</span></span>
<br />


#### <a name="to-install-the-f-20-runtime"></a><span data-ttu-id="d5ac8-122">Para instalar o tempo de execução do F # 2.0</span><span class="sxs-lookup"><span data-stu-id="d5ac8-122">To install the F# 2.0 runtime</span></span>

1. <span data-ttu-id="d5ac8-123">No painel de controle, escolha o **programas** link e, em seguida, escolha o **programas e recursos** link.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-123">In the Control Panel, choose the **Programs** link, and then choose the **Programs and Features** link.</span></span>
<br />

2. <span data-ttu-id="d5ac8-124">Na lista de programas instalados, selecione a edição do Visual Studio que você instalou e, em seguida, escolha o **alteração** botão.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-124">In the list of installed programs, choose the edition of Visual Studio that you installed, and then choose the **Change** button.</span></span>
<br />

3. <span data-ttu-id="d5ac8-125">Depois de inicia a instalação, escolha o **reparo** botão.</span><span class="sxs-lookup"><span data-stu-id="d5ac8-125">After setup starts, choose the **Repair** button.</span></span>
<br />  <span data-ttu-id="d5ac8-126">Para obter mais informações, consulte [instalar o Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).</span><span class="sxs-lookup"><span data-stu-id="d5ac8-126">For more information, see [Installing Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).</span></span>
<br />
## <a name="see-also"></a><span data-ttu-id="d5ac8-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5ac8-127">See Also</span></span>
[<span data-ttu-id="d5ac8-128">Visual F#</span><span class="sxs-lookup"><span data-stu-id="d5ac8-128">Visual F#</span></span>](../index.md)
