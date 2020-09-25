---
description: -main (opções do compilador C#)
title: -main (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: c27898de2a7cc2f3c01c51f8de1122e81b2233b4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194109"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="2b3a9-103">-main (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="2b3a9-103">-main (C# Compiler Options)</span></span>

<span data-ttu-id="2b3a9-104">Esta opção especifica a classe que contém o ponto de entrada para o programa, se mais de uma classe contiver um método **Main**.</span><span class="sxs-lookup"><span data-stu-id="2b3a9-104">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b3a9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b3a9-105">Syntax</span></span>

```console
-main:class
```

## <a name="arguments"></a><span data-ttu-id="2b3a9-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="2b3a9-106">Arguments</span></span>

 `class`  
 <span data-ttu-id="2b3a9-107">O tipo que contém o método **Main**.</span><span class="sxs-lookup"><span data-stu-id="2b3a9-107">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="2b3a9-108">O nome de classe informado deve ser totalmente qualificado. Ele deve incluir o namespace completo que contém a classe, seguido do nome de classe.</span><span class="sxs-lookup"><span data-stu-id="2b3a9-108">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="2b3a9-109">Por exemplo, quando o método `Main` é localizado dentro da classe `Program` no namespace `MyApplication.Core`, a opção do compilador deve ser `-main:MyApplication.Core.Program`.</span><span class="sxs-lookup"><span data-stu-id="2b3a9-109">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b3a9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b3a9-110">Remarks</span></span>

<span data-ttu-id="2b3a9-111">Se sua compilação incluir mais de um tipo com um método [Main](../../programming-guide/main-and-command-args/index.md), você poderá especificar qual tipo contém o método **Main** que deseja usar como o ponto de entrada para o programa.</span><span class="sxs-lookup"><span data-stu-id="2b3a9-111">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>

<span data-ttu-id="2b3a9-112">Essa opção é para uso durante a compilação de um arquivo *. exe* .</span><span class="sxs-lookup"><span data-stu-id="2b3a9-112">This option is for use when compiling an *.exe* file.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="2b3a9-113">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2b3a9-113">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="2b3a9-114">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="2b3a9-114">Open the project's **Properties** page.</span></span>

2. <span data-ttu-id="2b3a9-115">Clique na página de propriedades do **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="2b3a9-115">Click the **Application** property page.</span></span>

3. <span data-ttu-id="2b3a9-116">Modifique a propriedade **Objeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="2b3a9-116">Modify the **Startup object** property.</span></span>

    <span data-ttu-id="2b3a9-117">Para definir programaticamente essa opção do compilador, confira <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="2b3a9-117">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>

### <a name="to-set-this-compiler-option-by-manually-editing-the-csproj-file"></a><span data-ttu-id="2b3a9-118">Para definir essa opção de compilador editando manualmente o arquivo *. csproj*</span><span class="sxs-lookup"><span data-stu-id="2b3a9-118">To set this compiler option by manually editing the *.csproj* file</span></span>

<span data-ttu-id="2b3a9-119">Você pode definir essa opção editando o arquivo. csproj e adicionando um elemento `StartupObject` dentro da `PropertyGroup` seção.</span><span class="sxs-lookup"><span data-stu-id="2b3a9-119">You can set this option by editing the .csproj file and adding an element `StartupObject` inside the `PropertyGroup` section.</span></span> <span data-ttu-id="2b3a9-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2b3a9-120">For example:</span></span>

```xml
  <PropertyGroup>
    ...
    <StartupObject>MyApplication.Core.Program</StartupObject>
  </PropertyGroup>
```

## <a name="example"></a><span data-ttu-id="2b3a9-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b3a9-121">Example</span></span>

<span data-ttu-id="2b3a9-122">Compile `t2.cs` e `t3.cs`, especificando que o método **Main** será encontrado em `Test2`:</span><span class="sxs-lookup"><span data-stu-id="2b3a9-122">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>

```console
csc t2.cs t3.cs -main:Test2
```

## <a name="see-also"></a><span data-ttu-id="2b3a9-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="2b3a9-123">See also</span></span>

- [<span data-ttu-id="2b3a9-124">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="2b3a9-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2b3a9-125">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="2b3a9-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
