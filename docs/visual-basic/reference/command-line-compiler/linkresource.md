---
title: -linkresource
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 0315645eccdc899ac9cf4d0be105297e1fa2a4c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335488"
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic)
Cria um link a um recurso gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

ou  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Argumentos  
 `filename`  
 Necessária. O arquivo de recurso a ser vinculado ao assembly. Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").  
  
 `identifier`  
 Opcional. O nome lógico do recurso. O nome usado para carregar o recurso. O padrão é o nome do arquivo. Opcionalmente, você pode especificar se o arquivo é público ou privado no manifesto do assembly, por exemplo: `-linkres:filename.res,myname.res,public`. Por padrão, `filename` é público no assembly.  
  
## <a name="remarks"></a>Comentários  
 A opção `-linkresource` não incorpora o arquivo de recurso no arquivo de saída; Use a opção `-resource` para fazer isso.  
  
 A opção `-linkresource` requer uma das opções de `-target` diferentes de `-target:module`.  
  
 Se `filename` for um arquivo de recurso .NET Framework criado, por exemplo, pelo [Resgen. exe (gerador de arquivo de recurso)](../../../framework/tools/resgen-exe-resource-file-generator.md) ou no ambiente de desenvolvimento, ele poderá ser acessado com membros no namespace <xref:System.Resources>. (Para obter mais informações, consulte <xref:System.Resources.ResourceManager>.) Para acessar todos os outros recursos em tempo de execução, use os métodos que começam com `GetManifestResource` na classe <xref:System.Reflection.Assembly>.  
  
 O nome do arquivo pode ser qualquer formato de arquivo. Por exemplo, crie uma parte DLL nativa do assembly de maneira que possa ser instalada no cache de assembly global e acessado no código gerenciado no assembly.  
  
 A forma abreviada de `-linkresource` é `-linkres`.  
  
> [!NOTE]
> A opção `-linkresource` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente quando você compila a partir da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `in.vb` e links para o arquivo de recurso `rf.resource`.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-recurso (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
