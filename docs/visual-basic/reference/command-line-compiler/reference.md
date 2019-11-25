---
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 8b57affa05c77d8ed20bfead7de767a8dd994241
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348590"
---
# <a name="-reference-visual-basic"></a>-reference (Visual Basic)
Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-reference:fileList  
```

ou

```console
-r:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`fileList`|Necessário. Lista delimitada por vírgulas de nomes de arquivo do assembly. Se o nome do arquivo contém um espaço, coloque o nome entre aspas.|  
  
## <a name="remarks"></a>Comentários  
 The file(s) you import must contain assembly metadata. Only public types are visible outside the assembly. The [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.  
  
 If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:  
  
- Um tipo do Assembly A herda de um tipo ou implementa uma interface do Assembly B.  
  
- Um campo, propriedade, evento ou método que tem um tipo de retorno ou de parâmetro do Assembly B é invocado.  
  
 Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.  
  
 For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type. One example of how you can do this is to define an instance of the type. Other ways are available to resolve type names in an assembly for the compiler. For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.  
  
 The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default. Use `-noconfig` if you do not want the compiler to use Vbc.rsp.  
  
 A forma abreviada de `-reference` é `/r`.  
  
## <a name="example"></a>Exemplo  
 The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Público](../../../visual-basic/language-reference/modifiers/public.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
