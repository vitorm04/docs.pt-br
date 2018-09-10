---
title: -unsafe (opções do compilador C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 138c7cce83fd069f44025c57e52b2d01bcb23432
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518044"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="64155-102">-unsafe (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="64155-102">-unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="64155-103">A opção do compilador **-unsafe** permite que o código que usa a palavra-chave [unsafe](../../../csharp/language-reference/keywords/unsafe.md) seja compilado.</span><span class="sxs-lookup"><span data-stu-id="64155-103">The **-unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64155-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64155-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="64155-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="64155-105">Remarks</span></span>  
 <span data-ttu-id="64155-106">Para obter mais informações sobre código não seguro, consulte [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="64155-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="64155-107">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="64155-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="64155-108">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="64155-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="64155-109">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="64155-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="64155-110">Marque a caixa de seleção **Permitir código não seguro**.</span><span class="sxs-lookup"><span data-stu-id="64155-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="64155-111">Para adicionar essa opção em um arquivo csproj</span><span class="sxs-lookup"><span data-stu-id="64155-111">To add this option in a csproj file</span></span>

<span data-ttu-id="64155-112">Abra o arquivo .csproj de um projeto e adicione os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="64155-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="64155-113">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="64155-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64155-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64155-114">Example</span></span>  
 <span data-ttu-id="64155-115">Compile `in.cs` para o modo não seguro:</span><span class="sxs-lookup"><span data-stu-id="64155-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="64155-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64155-116">See Also</span></span>  

- [<span data-ttu-id="64155-117">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="64155-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="64155-118">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="64155-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
