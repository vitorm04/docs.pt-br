---
title: "-delaysign (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /delaysign
dev_langs:
- CSharp
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
caps.latest.revision: 16
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
ms.openlocfilehash: ce4c9fbb14081764985f3b02988dff9ee272c451
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="delaysign-c-compiler-options"></a><span data-ttu-id="028a5-102">/delaysign (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="028a5-102">/delaysign (C# Compiler Options)</span></span>
<span data-ttu-id="028a5-103">Essa opção faz com que o compilador reserve espaço no arquivo de saída para que uma assinatura digital possa ser adicionada mais tarde.</span><span class="sxs-lookup"><span data-stu-id="028a5-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="028a5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="028a5-104">Syntax</span></span>  
  
```console  
/delaysign[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="028a5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="028a5-105">Arguments</span></span>  
 <span data-ttu-id="028a5-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="028a5-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="028a5-107">Use **/delaysign-** se você quiser um assembly totalmente assinado.</span><span class="sxs-lookup"><span data-stu-id="028a5-107">Use **/delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="028a5-108">Use **/delaysign+** se você apenas deseja colocar a chave pública no assembly.</span><span class="sxs-lookup"><span data-stu-id="028a5-108">Use **/delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="028a5-109">O padrão é **/delaysign-**.</span><span class="sxs-lookup"><span data-stu-id="028a5-109">The default is **/delaysign-**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="028a5-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="028a5-110">Remarks</span></span>  
 <span data-ttu-id="028a5-111">A opção **/delaysign** não tem nenhum efeito a menos que seja usada com [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) ou [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="028a5-111">The **/delaysign** option has no effect unless used with [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) or [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span>  
  
 <span data-ttu-id="028a5-112">Quando você solicita um assembly totalmente assinado, o compilador usa o hash no arquivo que contém o manifesto (metadados de assembly) e sinaliza esse hash com a chave particular.</span><span class="sxs-lookup"><span data-stu-id="028a5-112">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="028a5-113">A assinatura digital resultante é armazenada no arquivo que contém o manifesto.</span><span class="sxs-lookup"><span data-stu-id="028a5-113">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="028a5-114">Quando um assembly é assinado com atraso, o compilador não calcula e armazena a assinatura, mas reserva o espaço no arquivo, de forma que a assinatura possa ser adicionada depois.</span><span class="sxs-lookup"><span data-stu-id="028a5-114">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="028a5-115">Por exemplo, o uso de **/delaysign+** permite que um testador coloque o assembly no cache global.</span><span class="sxs-lookup"><span data-stu-id="028a5-115">For example, using **/delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="028a5-116">Após o teste, é possível assinar completamente o assembly, colocando a chave particular no assembly com o utilitário [Assembly Linker](https://msdn.microsoft.com/library/c405shex).</span><span class="sxs-lookup"><span data-stu-id="028a5-116">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](https://msdn.microsoft.com/library/c405shex) utility.</span></span>  
  
 <span data-ttu-id="028a5-117">Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](https://msdn.microsoft.com/library/xwb8f617) e [Atraso na Assinatura de um Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="028a5-117">For more information, see [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="028a5-118">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="028a5-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="028a5-119">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="028a5-119">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="028a5-120">Modifique a propriedade **Apenas adiar a assinatura**.</span><span class="sxs-lookup"><span data-stu-id="028a5-120">Modify the **Delay sign only** property.</span></span>  
  
 <span data-ttu-id="028a5-121">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="028a5-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="028a5-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="028a5-122">See Also</span></span>  
 <span data-ttu-id="028a5-123">[Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="028a5-123">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="028a5-124">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="028a5-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

