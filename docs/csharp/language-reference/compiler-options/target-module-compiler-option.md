---
title: -target:module (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 25421df2e9306071ce3506aaf7affd1b259d1c32
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602446"
---
# <a name="-targetmodule-c-compiler-options"></a>-target:module (opções do compilador C#)
Essa opção faz com que o compilador não gere um manifesto do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Comentários  
 Por padrão, o arquivo de saída criado por meio da compilação com essa opção terá uma extensão .netmodule.  
  
 Um arquivo que não tem um manifesto do assembly não pode ser carregado pelo Common Language Runtime do .NET Framework. No entanto, esse arquivo pode ser incorporado no manifesto do assembly de um assembly por meio de [-addmodule](./addmodule-compiler-option.md).  
  
 Se mais de um módulo for criado em uma única compilação, tipos [internos](../keywords/internal.md) em um módulo estarão disponíveis para outros módulos na compilação. Quando o código em um módulo referenciar tipos `internal` em outro módulo, os dois módulos deverão ser incorporados em um manifesto do assembly, por meio de **-addmodule**.  
  
 Não há suporte para a criação de um módulo no ambiente de desenvolvimento do Visual Studio.  
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemplo  
 Compile `in.cs`, criando `in.netmodule`:  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Consulte também

- [-target (opções do compilador do C#)](./target-compiler-option.md)
- [Opções do compilador de C#](./index.md)
