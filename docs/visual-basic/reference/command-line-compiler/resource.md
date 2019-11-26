---
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: a781d543dd32ffb3d0ac0b11c544dbfd8cd5d806
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348562"
---
# <a name="-resource-visual-basic"></a>-resource (Visual Basic)
Embeds a managed resource in an assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

ou  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`filename`|Necessário. The name of the resource file to embed in the output file. By default, `filename` is public in the assembly. Enclose the file name in quotation marks (" ") if it contains a space.|  
|`identifier`|Opcional. The logical name for the resource; the name used to load it. O padrão é o nome do arquivo. Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>Comentários  
 Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.  
  
 If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information). To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.  
  
 A forma abreviada de `-resource` é `-res`.  
  
 For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
## <a name="example"></a>Exemplo  
 The following code compiles `In.vb` and attaches resource file `Rf.resource`.  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
