---
title: Direcionando o .NET Framework 2.0 no Windows 8
description: 'Saiba mais sobre direcionando a versão mais antiga do .NET Framework ao usar o F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 9b08cced63b46778a5081d4de710991a6299fd29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="targeting-older-versions-of-net"></a><span data-ttu-id="b8882-103">Direcionamento de versões mais antigas do .NET</span><span class="sxs-lookup"><span data-stu-id="b8882-103">Targeting Older Versions of .NET</span></span>

> [!NOTE]
<span data-ttu-id="b8882-104">Este artigo não é atualizado com o mais recente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8882-104">This article is not up to date with the latest Visual Studio.</span></span>  <span data-ttu-id="b8882-105">Ele será atualizado.</span><span class="sxs-lookup"><span data-stu-id="b8882-105">It will be updated.</span></span>

<span data-ttu-id="b8882-106">O seguinte erro pode aparecer se você tentar direcionar o .NET Framework 2.0, 3.0 ou 3.5 em F # projeto quando o Visual Studio está instalado no Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="b8882-106">The following error might appear if you try to target the .NET Framework 2.0, 3.0, or 3.5 in an F# project when Visual Studio is installed on Windows 8.1:</span></span> 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

<span data-ttu-id="b8882-107">Esse erro costuma ocorrer sob a seguinte combinação de condições:</span><span class="sxs-lookup"><span data-stu-id="b8882-107">This error is known to occur under the following combination of conditions:</span></span>


- <span data-ttu-id="b8882-108">Você instalou o Visual Studio Windows 8.1.</span><span class="sxs-lookup"><span data-stu-id="b8882-108">You installed Visual Studio on Windows 8.1.</span></span>
<br />

- <span data-ttu-id="b8882-109">Você não habilitar o .NET Framework 3.5 antes de instalar o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8882-109">You didn’t enable the .NET Framework 3.5 before you installed Visual Studio.</span></span>
<br />

- <span data-ttu-id="b8882-110">Seu projeto direcionado ao .NET Framework 2.0, 3.0 ou 3.5.</span><span class="sxs-lookup"><span data-stu-id="b8882-110">Your project targets the .NET Framework 2.0, 3.0, or 3.5.</span></span>
<br />

<span data-ttu-id="b8882-111">Quando você instala o Visual Studio, ele detecta as versões instaladas do .NET Framework e instala o tempo de execução 2.0 F # somente se o .NET Framework 3.5 está instalado e habilitado.</span><span class="sxs-lookup"><span data-stu-id="b8882-111">When you install Visual Studio, it detects the installed versions of the .NET Framework and installs the F# 2.0 Runtime only if the .NET Framework 3.5 is installed and enabled.</span></span>


## <a name="resolving-the-error"></a><span data-ttu-id="b8882-112">Resolver o erro</span><span class="sxs-lookup"><span data-stu-id="b8882-112">Resolving the Error</span></span>
<span data-ttu-id="b8882-113">Para resolver esse erro, você pode ou uma versão mais recente do .NET Framework de destino, ou você pode habilitar o .NET Framework 3.5 no Windows 8.1 e, em seguida, instalar o runtime do F # 2.0 executando o programa de instalação do Visual Studio com o **reparo** opção.</span><span class="sxs-lookup"><span data-stu-id="b8882-113">To resolve this error, you can either target a newer version of the .NET Framework, or you can enable the .NET Framework 3.5 on Windows 8.1 and then install the F# 2.0 runtime by running the setup program for Visual Studio with the **Repair** option.</span></span>


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a><span data-ttu-id="b8882-114">Para habilitar o .NET Framework 3.5 no Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="b8882-114">To enable the .NET Framework 3.5 on Windows 8.1</span></span>

1. <span data-ttu-id="b8882-115">Sobre o **iniciar** tela, comece a digitar **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="b8882-115">On the **Start** screen, start to enter **Control Panel**.</span></span>
<br />  <span data-ttu-id="b8882-116">Quando você insere esse nome, o **painel de controle** aparece sob o **aplicativos** título.</span><span class="sxs-lookup"><span data-stu-id="b8882-116">As you enter that name, the **Control Panel** icon appears under the **Apps** heading.</span></span>
<br />

2. <span data-ttu-id="b8882-117">Escolha o **painel de controle** ícone, escolha o **programas** ícone e, em seguida, escolha o **ativar recursos do Windows ou desativar** link.</span><span class="sxs-lookup"><span data-stu-id="b8882-117">Choose the **Control Panel** icon, choose the **Programs** icon, and then choose the **Turn Windows features on or off** link.</span></span>
<br />

3. <span data-ttu-id="b8882-118">Verifique se o **.NET Framework 3.5 (inclui .NET 2.0 e 3.0)** caixa de seleção está selecionada e, em seguida, escolha o **Okey** botão.</span><span class="sxs-lookup"><span data-stu-id="b8882-118">Make sure that the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box is selected, and then choose the **OK** button.</span></span>
<br />  <span data-ttu-id="b8882-119">Você não precisa selecionar as caixas de seleção para todos os nós filho para os componentes opcionais do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8882-119">You don’t need to select the check boxes for any child nodes for optional components of the .NET Framework.</span></span>
<br />  <span data-ttu-id="b8882-120">O .NET Framework 3.5 está habilitada, se já não.</span><span class="sxs-lookup"><span data-stu-id="b8882-120">The .NET Framework 3.5 is enabled if it wasn't already.</span></span>
<br />


#### <a name="to-install-the-f-20-runtime"></a><span data-ttu-id="b8882-121">Para instalar o tempo de execução do F # 2.0</span><span class="sxs-lookup"><span data-stu-id="b8882-121">To install the F# 2.0 runtime</span></span>

1. <span data-ttu-id="b8882-122">No painel de controle, escolha o **programas** link e, em seguida, escolha o **programas e recursos** link.</span><span class="sxs-lookup"><span data-stu-id="b8882-122">In the Control Panel, choose the **Programs** link, and then choose the **Programs and Features** link.</span></span>
<br />

2. <span data-ttu-id="b8882-123">Na lista de programas instalados, selecione a edição do Visual Studio que você instalou e, em seguida, escolha o **alteração** botão.</span><span class="sxs-lookup"><span data-stu-id="b8882-123">In the list of installed programs, choose the edition of Visual Studio that you installed, and then choose the **Change** button.</span></span>
<br />

3. <span data-ttu-id="b8882-124">Depois de inicia a instalação, escolha o **reparo** botão.</span><span class="sxs-lookup"><span data-stu-id="b8882-124">After setup starts, choose the **Repair** button.</span></span>
<br />  <span data-ttu-id="b8882-125">Para obter mais informações, consulte [instalar o Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).</span><span class="sxs-lookup"><span data-stu-id="b8882-125">For more information, see [Installing Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).</span></span>
<br />
## <a name="see-also"></a><span data-ttu-id="b8882-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8882-126">See Also</span></span>
[<span data-ttu-id="b8882-127">Visual F#</span><span class="sxs-lookup"><span data-stu-id="b8882-127">Visual F#</span></span>](../index.md)
