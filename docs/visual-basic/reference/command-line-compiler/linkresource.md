---
title: /linkresource (Visual Basic) | Documentos do Microsoft
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
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fafde6563340189108a879b82e7e880aca690b39
ms.lasthandoff: 03/13/2017

---
# <a name="linkresource-visual-basic"></a>/linkresource (Visual Basic)
Cria um link a um recurso gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Necessário. O arquivo de recurso para vincular ao assembly. Se o nome do arquivo contém um espaço, coloque o nome entre aspas ("").  
  
 `identifier`  
 Opcional. O nome lógico para o recurso. O nome que é usado para carregar o recurso. O padrão é o nome do arquivo. Opcionalmente, você pode especificar se o arquivo é pública ou privada no manifesto do assembly, por exemplo: `/linkres:filename.res,myname.res,public`. Por padrão, `filename` é público no assembly.  
  
## <a name="remarks"></a>Comentários  
 O `/linkresource` opção não insere o arquivo de recurso no arquivo de saída; use o `/resource` como fazer isso.  
  
 O `/linkresource` opção requer um do `/target` diferente de opções `/target:module`.  
  
 Se `filename` é um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] arquivo de recurso criado, por exemplo, pelo [Resgen.exe (gerador de arquivo)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou no ambiente de desenvolvimento, ele pode ser acessado com membros de <xref:System.Resources>namespace.</xref:System.Resources> (Para obter mais informações, consulte <xref:System.Resources.ResourceManager>.)</xref:System.Resources.ResourceManager> Para acessar todos os outros recursos em tempo de execução, use os métodos que começam com `GetManifestResource` na <xref:System.Reflection.Assembly>classe.</xref:System.Reflection.Assembly>  
  
 O nome do arquivo pode ser qualquer formato de arquivo. Por exemplo, você talvez queira fazer uma parte DLL nativa do assembly, para que possa ser instalado no cache de assembly global e acessado a partir do código gerenciado no assembly.  
  
 A forma abreviada do `/linkresource` é `/linkres`.  
  
> [!NOTE]
>  O `/linkresource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente quando você compilar na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `In.vb` e links para o arquivo de recurso `Rf.resource`.  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [/Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
