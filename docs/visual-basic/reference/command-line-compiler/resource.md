---
title: /Resource (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b46800322fd03eb2578cc558cc1d9bb78550aa61
ms.lasthandoff: 03/13/2017

---
# <a name="resource-visual-basic"></a>/resource (Visual Basic)
Insere um recurso gerenciado em um assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/resource:filename[,identifier[,public|private]]  
' -or-  
/res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`filename`|Necessário. O nome do arquivo de recurso incorporado no arquivo de saída. Por padrão, `filename` é público no assembly. Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.|  
|`identifier`|Opcional. O nome lógico para o recurso. o nome usado para carregá-lo. O padrão é o nome do arquivo. Opcionalmente, você pode especificar se o recurso é pública ou privada no manifesto do assembly, assim como acontece com o seguinte: `/res:``filename.res`,`myname.res`,`public`|  
  
## <a name="remarks"></a>Comentários  
 Use `/linkresource` para vincular um recurso a um assembly sem colocar o arquivo de recurso no arquivo de saída.  
  
 Se `filename` é um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] arquivo de recurso criado, por exemplo, pelo [Resgen.exe (gerador de arquivo)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou no ambiente de desenvolvimento, ele pode ser acessado com membros de <xref:System.Resources>namespace (consulte <xref:System.Resources.ResourceManager>para obter mais informações).</xref:System.Resources.ResourceManager> </xref:System.Resources> Para acessar todos os outros recursos em tempo de execução, use um dos seguintes métodos: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, ou <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</xref:System.Reflection.Assembly.GetManifestResourceStream%2A> </xref:System.Reflection.Assembly.GetManifestResourceNames%2A> </xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>  
  
 A forma abreviada do `/resource` é `/res`.  
  
 Para obter informações sobre como definir `/resource` no IDE do Visual Studio, consulte [recursos de gerenciamento de aplicativo (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet).  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `In.vb` e anexa arquivos de recurso `Rf.resource`.  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)   
 [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)   
 [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
