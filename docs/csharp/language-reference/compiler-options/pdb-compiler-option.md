---
title: -pdb (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 9f8158ec0d8de2b9249c4f69830c37480c34b390
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217422"
---
# <a name="-pdb-c-compiler-options"></a>-pdb (opções do compilador C#)
A opção do compilador **-pdb** especifica o nome e o local do arquivo de símbolos de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 O nome e o local do arquivo de símbolos de depuração.  
  
## <a name="remarks"></a>Comentários  
 Ao especificar [-debug (Opções do compilador do C#)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), o compilador criará um arquivo .pdb no mesmo diretório em que o compilador criará o arquivo de saída (.exe ou .dll) com um nome de arquivo que é o mesmo que o nome do arquivo de saída.  
  
 O **-pdb** permite que você especifique um nome de arquivo não padrão e um local para o arquivo .pdb.  
  
 Essa opção do compilador não pode ser definida no ambiente de desenvolvimento do Visual Studio nem pode ser alterada por meio de programação.  
  
## <a name="example"></a>Exemplo  
 Compile `t.cs` e crie um arquivo .pdb chamado tt.pdb:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
