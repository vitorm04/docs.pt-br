---
title: -addmodule
ms.date: 03/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c17d5541fe2d02ba88f4c5ef259b2248f371dfe5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-addmodule"></a>-addmodule
Faz com que o compilador verifique todos os tipos de informações de arquivos especificados disponíveis para o projeto que você está compilando.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Necessário. Lista delimitada por vírgulas de arquivos que contêm metadados, mas não contêm manifestos de assembly. Nomes de arquivos que contenham espaços devem ficar entre aspas ("").  
  
## <a name="remarks"></a>Comentários  
 Os arquivos listados pelo `fileList` parâmetro deve ser criado com o `-target:module` opção, ou com o equivalente do compilador outro para `-target:module`.  
  
 Todos os módulos adicionados com `-addmodule` deve estar no mesmo diretório que o arquivo de saída em tempo de execução. Ou seja, você pode especificar um módulo em qualquer diretório no tempo de compilação, mas o módulo deve estar no diretório de aplicativo em tempo de execução. Se não for, você receberá um <xref:System.TypeLoadException> erro.  
  
 Se você especificar (implícita ou explicitamente) qualquer[-alvo (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) opção diferente de `-target:module` com `-addmodule`, os arquivos que você passa para `-addmodule` se tornam parte do assembly do projeto. Um assembly é necessário para executar um arquivo de saída que tem um ou mais arquivos adicionados com `-addmodule`.  
  
 Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) importar metadados de um arquivo que contém um assembly.  
  
> [!NOTE]
>  O `-addmodule` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir cria um módulo.  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 O código a seguir importa os tipos do módulo.  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 Quando você executa `t1`, ele produz `802`.  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-alvo (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-referência (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
