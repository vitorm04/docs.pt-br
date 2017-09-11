---
title: "-pdb (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /pdb
dev_langs:
- CSharp
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: 8
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
ms.openlocfilehash: 7c72c12347a9096aeed063b84310356cb07b49c3
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="pdb-c-compiler-options"></a><span data-ttu-id="3d788-102">/pdb (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="3d788-102">/pdb (C# Compiler Options)</span></span>
<span data-ttu-id="3d788-103">A opção do compilador **/pdb** especifica o nome e o local do arquivo de símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="3d788-103">The **/pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d788-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d788-104">Syntax</span></span>  
  
```console  
/pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="3d788-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3d788-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="3d788-106">O nome e o local do arquivo de símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="3d788-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d788-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3d788-107">Remarks</span></span>  
 <span data-ttu-id="3d788-108">Quando você especificar [/debug (Opções do compilador C#)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), o compilador criará um arquivo .pdb no mesmo diretório em que o compilador criará o arquivo de saída (.exe ou .dll) com um nome de arquivo que é o mesmo que o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="3d788-108">When you specify [/debug (C# Compiler Options)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="3d788-109">O **/pdb** permite que você especifique um nome de arquivo não padrão e um local para o arquivo .pdb.</span><span class="sxs-lookup"><span data-stu-id="3d788-109">**/pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="3d788-110">Essa opção do compilador não pode ser definida no ambiente de desenvolvimento do Visual Studio nem pode ser alterada por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="3d788-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d788-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3d788-111">Example</span></span>  
 <span data-ttu-id="3d788-112">Compile `t.cs` e crie um arquivo .pdb chamado tt.pdb:</span><span class="sxs-lookup"><span data-stu-id="3d788-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc /debug /pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d788-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d788-113">See Also</span></span>  
 <span data-ttu-id="3d788-114">[Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="3d788-114">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="3d788-115">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="3d788-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

