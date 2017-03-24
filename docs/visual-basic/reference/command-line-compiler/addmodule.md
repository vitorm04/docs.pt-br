---
title: /addmodule | Documentos do Microsoft
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
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: 14
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
ms.openlocfilehash: 949962905ec933dc42301bf8c21654e73dbe2f70
ms.lasthandoff: 03/13/2017

---
# <a name="addmodule"></a>/addmodule
Faz com que o compilador verifique todos os tipos de informações de arquivos especificados disponíveis para o projeto que você está compilando.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Necessário. Lista delimitada por vírgulas de arquivos que contêm metadados, mas não contêm manifestos assembly. Nomes de arquivo que contêm espaços devem estar entre aspas ("").  
  
## <a name="remarks"></a>Comentários  
 Os arquivos listados pelo `fileList` parâmetro deve ser criado com o `/target:module` opção, ou com o equivalente do outro compilador `/target:module`.  
  
 Todos os módulos adicionados com `/addmodule` deve estar no mesmo diretório que o arquivo de saída em tempo de execução. Ou seja, você pode especificar um módulo em qualquer diretório em tempo de compilação, mas o módulo deve estar no diretório do aplicativo em tempo de execução. Se não for, você obterá um <xref:System.TypeLoadException>erro.</xref:System.TypeLoadException>  
  
 Se você especificar (implícita ou explicitamente) qualquer[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) opção diferente de `/target:module` com `/addmodule`, os arquivos que você passar para `/addmodule` se tornam parte do assembly do projeto. Um assembly é necessário para executar um arquivo de saída que tem um ou mais arquivos adicionados com `/addmodule`.  
  
 Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) para importar metadados de um arquivo que contém um assembly.  
  
> [!NOTE]
>  O `/addmodule` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir cria um módulo.  
  
 [!code-vb[47 VbVbalrCompiler](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 O código a seguir importa tipos do módulo.  
  
 [!code-vb[48 VbVbalrCompiler](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 Quando você executa `t1`, ele produz `802`.  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
