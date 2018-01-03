---
title: /imports (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cdb7cff2221930113d6b49a640da0844f175f1b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="imports-visual-basic"></a>/imports (Visual Basic)
Importa namespaces de um assembly específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`namespaceList`|Necessário. Lista delimitada por vírgulas de namespaces a serem importados.|  
  
## <a name="remarks"></a>Comentários  
 O `/imports` opção importa qualquer namespace definido dentro do conjunto atual de arquivos de origem ou de qualquer assembly referenciado.  
  
 Os membros no namespace especificado com `/imports` estão disponíveis para todos os arquivos de código-fonte na compilação. Use o [instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para utilizar um namespace em um arquivo de código-fonte única.  
  
|Para configurar /Imports no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Referências**.<br />3.  Insira o nome do namespace na caixa ao lado de **Add User Import** botão.<br />4.  Clique o **Add User Import** botão.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila quando `/imports:system` for especificado.  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Referências e a Instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
