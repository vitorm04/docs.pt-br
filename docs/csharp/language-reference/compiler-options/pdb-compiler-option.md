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
# <a name="-pdb-c-compiler-options"></a>-pdb (opções do compilador C#)
A opção do compilador **-pdb** especifica o nome e o local do arquivo de símbolos de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a>Argumentos  
 `filename`  
 O nome e o local do arquivo de símbolos de depuração.  
  
## <a name="remarks"></a>Comentários  
 Ao especificar [-debug (Opções do compilador do C#)](./debug-compiler-option.md), o compilador criará um arquivo .pdb no mesmo diretório em que o compilador criará o arquivo de saída (.exe ou .dll) com um nome de arquivo que é o mesmo que o nome do arquivo de saída.  
  
 O **-pdb** permite que você especifique um nome de arquivo não padrão e um local para o arquivo .pdb.  
  
 Essa opção do compilador não pode ser definida no ambiente de desenvolvimento do Visual Studio nem pode ser alterada por meio de programação.  
  
## <a name="example"></a>Exemplo  
 Compile `t.cs` e crie um arquivo .pdb chamado tt.pdb:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Confira também

- [Opções do compilador C#](./index.md)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
