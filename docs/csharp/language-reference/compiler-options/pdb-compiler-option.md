---
title: "-pdb (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7528283765c2b6f4a9d5e84015526a95938a6281
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="77116-102">-pdb (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="77116-102">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="77116-103">A opção do compilador **-pdb** especifica o nome e o local do arquivo de símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="77116-103">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77116-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77116-104">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="77116-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="77116-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="77116-106">O nome e o local do arquivo de símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="77116-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77116-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="77116-107">Remarks</span></span>  
 <span data-ttu-id="77116-108">Ao especificar [-debug (Opções do compilador do C#)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), o compilador criará um arquivo .pdb no mesmo diretório em que o compilador criará o arquivo de saída (.exe ou .dll) com um nome de arquivo que é o mesmo que o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="77116-108">When you specify [-debug (C# Compiler Options)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="77116-109">O **-pdb** permite que você especifique um nome de arquivo não padrão e um local para o arquivo .pdb.</span><span class="sxs-lookup"><span data-stu-id="77116-109">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="77116-110">Essa opção do compilador não pode ser definida no ambiente de desenvolvimento do Visual Studio nem pode ser alterada por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="77116-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77116-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77116-111">Example</span></span>  
 <span data-ttu-id="77116-112">Compile `t.cs` e crie um arquivo .pdb chamado tt.pdb:</span><span class="sxs-lookup"><span data-stu-id="77116-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="77116-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77116-113">See Also</span></span>  
 [<span data-ttu-id="77116-114">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="77116-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="77116-115">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="77116-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
