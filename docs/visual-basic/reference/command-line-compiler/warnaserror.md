---
title: /warnaserror (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d472795affe0df098d1551daf51a2f0ae20723ba
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="warnaserror-visual-basic"></a>/warnaserror (Visual Basic)
Faz com que o compilador trate a primeira ocorrência de um aviso como erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|+ &#124; -|Opcional. Por padrão, `/warnaserror-` está em vigor; avisos não impedem que o compilador gera um arquivo de saída. O `/warnaserror` opção, que é o mesmo como `/warnaserror+`, faz com que avisos a serem tratados como erros.|  
|`numberList`|Opcional. Lista delimitada por vírgulas da identificação do aviso numera a qual o `/warnaserror` opção se aplica. Se nenhuma ID de aviso for especificada, o `/warnaserror` opção se aplica a todos os avisos.|  
  
## <a name="remarks"></a>Comentários  
 O `/warnaserror` opção trata todos os avisos como erros. Quaisquer mensagens que seriam normalmente ser relatadas como avisos em vez disso, são relatados como erros. O compilador relata ocorrências subsequentes do mesmo aviso como avisos.  
  
 Por padrão, `/warnaserror-` está em vigor, o que faz com que os avisos sejam apenas informativos. O `/warnaserror` opção, que é o mesmo como `/warnaserror+`, faz com que avisos a serem tratados como erros.  
  
 Se você quiser apenas alguns avisos específicos a serem tratados como erros, você pode especificar uma lista separada por vírgulas de números de avisos a serem tratados como erros.  
  
> [!NOTE]
>  O `/warnaserror` opção não controla como os avisos são exibidos. Use o [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) opção para desativar avisos.  
  
|Para definir /warnaserror para tratar todos os avisos como erros no IDE do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Verifique se o **desativar todos os avisos** caixa de seleção está desmarcada.<br />4.  Verifique o **trate todos os avisos como erros** caixa de seleção.|  
  
|Para definir /warnaserror para tratar avisos específicos como erros no IDE do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.<br />2.  Clique na guia **Compilar**.<br />3.  Verifique se o **desativar todos os avisos** caixa de seleção está desmarcada.<br />4.  Verifique se o **trate todos os avisos como erros** caixa de seleção está desmarcada.<br />5.  Selecione **erro** do **notificação** coluna adjacente ao aviso que deve ser tratado como um erro.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `In.vb` e direciona o compilador para exibir um erro para a primeira ocorrência de cada aviso que ele encontra.  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e trata apenas o aviso de variáveis locais não utilizadas (42024) como um erro.  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
