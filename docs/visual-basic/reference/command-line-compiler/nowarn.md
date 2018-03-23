---
title: -nowarn
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d2f3f15ef12b24b8baedc9db59e772aa9eb073bc
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-nowarn"></a>-nowarn
Suprime a capacidade do compilador para gerar avisos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`numberList`|Opcional. Lista delimitada por vírgulas de números de ID de aviso que o compilador deve eliminar. Se o aviso identificações não for especificado, todos os avisos são suprimidos.|  
  
## <a name="remarks"></a>Comentários  
 O `-nowarn` opção faz com que o compilador não gere avisos. Para suprimir um aviso individual, forneça a ID do aviso para o `-nowarn` opção após os dois-pontos. Separe vários números de aviso com vírgulas.  
  
 Você precisa especificar somente a parte numérica do identificador de aviso. Por exemplo, se você desejar suprimir BC42024, o aviso para variáveis locais não utilizados, especificar `-nowarn:42024`.  
  
 Para obter mais informações sobre os números de ID de aviso, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Para definir - nowarn no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Selecione o **desativar todos os avisos** caixa de seleção para desativar todos os avisos.<br />     - ou -<br />     Para desativar um aviso específico, clique em **nenhum** da lista suspensa adjacente ao aviso.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e não exibe avisos.  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e não exibe os avisos para variáveis locais não utilizadas (42024).  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
