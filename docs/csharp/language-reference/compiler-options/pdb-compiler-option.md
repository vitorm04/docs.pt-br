---
description: -pdb (opções do compilador C#)
title: -pdb (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 0dcafd0fd260488922c74a2330b312e80467e779
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124910"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="6cba4-103">-pdb (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="6cba4-103">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="6cba4-104">A opção do compilador **-pdb** especifica o nome e o local do arquivo de símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="6cba4-104">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cba4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6cba4-105">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="6cba4-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="6cba4-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="6cba4-107">O nome e o local do arquivo de símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="6cba4-107">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cba4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="6cba4-108">Remarks</span></span>  
 <span data-ttu-id="6cba4-109">Ao especificar [-debug (Opções do compilador do C#)](./debug-compiler-option.md), o compilador criará um arquivo .pdb no mesmo diretório em que o compilador criará o arquivo de saída (.exe ou .dll) com um nome de arquivo que é o mesmo que o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="6cba4-109">When you specify [-debug (C# Compiler Options)](./debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="6cba4-110">O **-pdb** permite que você especifique um nome de arquivo não padrão e um local para o arquivo .pdb.</span><span class="sxs-lookup"><span data-stu-id="6cba4-110">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="6cba4-111">Essa opção do compilador não pode ser definida no ambiente de desenvolvimento do Visual Studio nem pode ser alterada por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="6cba4-111">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cba4-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6cba4-112">Example</span></span>  
 <span data-ttu-id="6cba4-113">Compile `t.cs` e crie um arquivo .pdb chamado tt.pdb:</span><span class="sxs-lookup"><span data-stu-id="6cba4-113">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6cba4-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="6cba4-114">See also</span></span>

- [<span data-ttu-id="6cba4-115">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="6cba4-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6cba4-116">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="6cba4-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
