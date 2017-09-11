---
title: "-unsafe (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /unsafe
dev_langs:
- CSharp
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.assetid: fdb77ed9-da03-45bd-bb7f-250704da1bcc
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8f285af57d6a06d38d20b2c28e4a637fbc3ecf2c
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="unsafe-c-compiler-options"></a><span data-ttu-id="d0962-102">/unsafe (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="d0962-102">/unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="d0962-103">A opção do compilador **/unsafe** permite que o código que usa a palavra-chave [unsafe](../../../csharp/language-reference/keywords/unsafe.md) seja compilado.</span><span class="sxs-lookup"><span data-stu-id="d0962-103">The **/unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0962-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0962-104">Syntax</span></span>  
  
```console  
/unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="d0962-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0962-105">Remarks</span></span>  
 <span data-ttu-id="d0962-106">Para obter mais informações sobre código não seguro, consulte [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="d0962-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d0962-107">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d0962-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="d0962-108">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="d0962-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="d0962-109">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="d0962-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="d0962-110">Marque a caixa de seleção **Permitir código não seguro**.</span><span class="sxs-lookup"><span data-stu-id="d0962-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
 <span data-ttu-id="d0962-111">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="d0962-111">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0962-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0962-112">Example</span></span>  
 <span data-ttu-id="d0962-113">Compile `in.cs` para o modo não seguro:</span><span class="sxs-lookup"><span data-stu-id="d0962-113">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc /unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0962-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0962-114">See Also</span></span>  
 <span data-ttu-id="d0962-115">[Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="d0962-115">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="d0962-116">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="d0962-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

