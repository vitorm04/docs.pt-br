---
title: /warnaserror (Visual Basic) | Documentos do Microsoft
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
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: 18
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
ms.openlocfilehash: 28f232b1ad8200455550f2f4c1204818c8b143ab
ms.lasthandoff: 03/13/2017

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
|+ &#124; -|Opcional. Por padrão, `/warnaserror-` está em vigor; avisos não impedem o compilador de produzir um arquivo de saída. O `/warnaserror` opção, que é o mesmo como `/warnaserror+`, faz com que os avisos sejam tratados como erros.|  
|`numberList`|Opcional. Lista delimitada por vírgulas da identificação do aviso numera a qual o `/warnaserror` opção se aplica. Se nenhuma identificação de aviso for especificada, o `/warnaserror` opção se aplica a todos os avisos.|  
  
## <a name="remarks"></a>Comentários  
 O `/warnaserror` opção trata todos os avisos como erros. Quaisquer mensagens que seriam normalmente ser relatadas como avisos em vez disso, são relatados como erros. O compilador relata ocorrências subsequentes ao mesmo aviso como avisos.  
  
 Por padrão, `/warnaserror-` está em vigor, o que faz com que os avisos sejam apenas informativos. O `/warnaserror` opção, que é o mesmo como `/warnaserror+`, faz com que os avisos sejam tratados como erros.  
  
 Se você quiser apenas alguns avisos específicos a serem tratados como erros, você pode especificar uma lista separada por vírgulas de números de aviso para tratar como erros.  
  
> [!NOTE]
>  O `/warnaserror` opção controla como os avisos são exibidos. Use o [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) opção para desativar avisos.  
  
|Para definir /warnaserror para tratar todos os avisos como erros no IDE do Visual Studio|  
|---|  
|1.  Tenha um projeto selecionado no **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique na guia **Compilar**.<br />3.  Verifique se o **desativar todos os avisos** caixa de seleção está desmarcada.<br />4.  Verifique o **tratar todos os avisos como erros** caixa de seleção.|  
  
|Para definir /warnaserror para tratar avisos específicos como erros no IDE do Visual Studio|  
|---|  
|1.  Tenha um projeto selecionado no **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**.<br />2.  Clique na guia **Compilar**.<br />3.  Verifique se o **desativar todos os avisos** caixa de seleção está desmarcada.<br />4.  Verifique se o **tratar todos os avisos como erros** caixa de seleção está desmarcada.<br />5.  Selecione **erro** do **notificação** coluna adjacente ao aviso que deve ser tratado como um erro.|  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `In.vb` e direciona o compilador para exibir um erro para a primeira ocorrência de cada aviso que ele encontra.  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` e trata apenas o aviso de variáveis locais não utilizadas (42024) como um erro.  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)
