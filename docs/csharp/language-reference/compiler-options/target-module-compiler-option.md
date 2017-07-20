---
title: "-target:module (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /target:module
dev_langs:
- CSharp
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
caps.latest.revision: 11
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7bb78acab13b93d65ffdaf6c8b9c0f3a5a1bcd2a
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="targetmodule-c-compiler-options"></a>/target:module (opções do compilador C#)
Essa opção faz com que o compilador não gere um manifesto do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/target:module  
```  
  
## <a name="remarks"></a>Comentários  
 Por padrão, o arquivo de saída criado por meio da compilação com essa opção terá uma extensão .netmodule.  
  
 Um arquivo que não tem um manifesto do assembly não pode ser carregado pelo Common Language Runtime do .NET Framework. No entanto, esse arquivo pode ser incorporado no manifesto do assembly de um assembly por meio de [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Se mais de um módulo for criado em uma única compilação, tipos [internos](../../../csharp/language-reference/keywords/internal.md) em um módulo estarão disponíveis para outros módulos na compilação. Quando o código em um módulo referenciar tipos `internal` em outro módulo, então ambos os módulos deverão ser incorporados em um manifesto do assembly, por meio de **/addmodule**.  
  
 Não há suporte para a criação de um módulo no ambiente de desenvolvimento do Visual Studio.  
  
 Para obter informações sobre como definir essa opção do compilador de maneira programática, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemplo  
 Compile `in.cs`, criando `in.netmodule`:  
  
```console  
csc /target:module in.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [/target (Opções do compilador C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
