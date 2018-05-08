---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 38740ed7ab7904feb2ca95eb70c916fbdbaef71e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic)
Cria um link a um recurso gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Obrigatório. O arquivo de recurso para vincular ao assembly. Se o nome do arquivo contém um espaço, coloque o nome entre aspas ("").  
  
 `identifier`  
 Opcional. O nome lógico para o recurso. O nome que é usado para carregar o recurso. O padrão é o nome do arquivo. Opcionalmente, você pode especificar se o arquivo é pública ou privada no manifesto do assembly, por exemplo: `-linkres:filename.res,myname.res,public`. Por padrão, `filename` é público no assembly.  
  
## <a name="remarks"></a>Comentários  
 O `-linkresource` opção não insere o arquivo de recurso no arquivo de saída; use o `-resource` opção para fazer isso.  
  
 O `-linkresource` opção requer um do `-target` opções diferentes de `-target:module`.  
  
 Se `filename` é um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recursos criado, por exemplo, pelo [Resgen.exe (gerador de arquivo)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou no ambiente de desenvolvimento, ele pode ser acessado com membros no <xref:System.Resources> namespace. (Para obter mais informações, consulte <xref:System.Resources.ResourceManager>.) Para acessar todos os outros recursos em tempo de execução, use os métodos que começam com `GetManifestResource` no <xref:System.Reflection.Assembly> classe.  
  
 O nome do arquivo pode ser qualquer formato de arquivo. Por exemplo, crie uma parte DLL nativa do assembly de maneira que possa ser instalada no cache de assembly global e acessado no código gerenciado no assembly.  
  
 A forma abreviada de `-linkresource` é `-linkres`.  
  
> [!NOTE]
>  O `-linkresource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível apenas quando você compila na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `in.vb` e links para o arquivo de recurso `rf.resource`.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-alvo (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-recurso (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
