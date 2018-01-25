---
title: "-recurse (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b50454112bc7aee6c3e0f8fe674e8727ca9e49be
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-recurse-c-compiler-options"></a>-recurse (opções do compilador C#)
A opção -recurse permite compilar arquivos de código-fonte em todos os diretórios filho do diretório especificado (dir) ou do diretório do projeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir` (opcional)  
 O diretório no qual você deseja que a pesquisa comece. Se ele não for especificado, a pesquisa começará no diretório do projeto.  
  
 `file`  
 Os arquivos a serem pesquisados. São permitidos caracteres curinga.  
  
## <a name="remarks"></a>Comentários  
 A opção **-recurse** permite compilar arquivos de código-fonte em todos os diretórios filho do diretório especificado (`dir`) ou do diretório do projeto.  
  
 É possível usar curingas em um nome de arquivo para compilar todos os arquivos correspondentes no diretório do projeto sem usar **-recurse**.  
  
 Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.  
  
## <a name="example"></a>Exemplo  
 Compila todos os arquivos C# no diretório atual:  
  
```console  
csc *.cs  
```  
  
 Compila todos os arquivos C# no diretório dir1\dir2 e quaisquer diretórios abaixo dele e gera dir2.dll:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
