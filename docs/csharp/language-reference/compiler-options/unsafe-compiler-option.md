---
title: -unsafe (opções do compilador C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 146299fda103567b111c66400c17edf36addd843
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877987"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="5eb92-102">-unsafe (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="5eb92-102">-unsafe (C# Compiler Options)</span></span>

<span data-ttu-id="5eb92-103">A opção do compilador **-unsafe** permite que o código que usa a palavra-chave [unsafe](../keywords/unsafe.md) seja compilado.</span><span class="sxs-lookup"><span data-stu-id="5eb92-103">The **-unsafe** compiler option allows code that uses the [unsafe](../keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eb92-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5eb92-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="5eb92-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="5eb92-105">Remarks</span></span>

<span data-ttu-id="5eb92-106">Para obter mais informações sobre código não seguro, consulte [Código não seguro e ponteiros](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="5eb92-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5eb92-107">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5eb92-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="5eb92-108">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="5eb92-108">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="5eb92-109">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="5eb92-109">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="5eb92-110">Marque a caixa de seleção **Permitir código não seguro**.</span><span class="sxs-lookup"><span data-stu-id="5eb92-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="5eb92-111">Para adicionar essa opção em um arquivo csproj</span><span class="sxs-lookup"><span data-stu-id="5eb92-111">To add this option in a csproj file</span></span>

<span data-ttu-id="5eb92-112">Abra o arquivo .csproj de um projeto e adicione os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="5eb92-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="5eb92-113">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="5eb92-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5eb92-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5eb92-114">Example</span></span>

<span data-ttu-id="5eb92-115">Compile `in.cs` para o modo não seguro:</span><span class="sxs-lookup"><span data-stu-id="5eb92-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="5eb92-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5eb92-116">See also</span></span>

- [<span data-ttu-id="5eb92-117">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="5eb92-117">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="5eb92-118">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="5eb92-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
