---
title: /nowarn | Documentos do Microsoft
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
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: 15
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
ms.openlocfilehash: 61b145a9eb95f5357c7aa2983a96c31e8f2cef6a
ms.lasthandoff: 03/13/2017

---
# <a name="nowarn"></a>/nowarn
Suprime a capacidade do compilador para gerar avisos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`numberList`|Opcional. Lista delimitada por vírgula dos números de identificação de aviso que o compilador deve eliminar. Se o aviso identificações não for especificado, todos os avisos são suprimidos.|  
  
## <a name="remarks"></a>Comentários  
 O `/nowarn` opção faz com que o compilador não gere avisos. Para suprimir um aviso individual, forneça a identificação de aviso para o `/nowarn` opção após os dois-pontos. Separe vários números de aviso com vírgulas.  
  
 Você precisa especificar somente a parte numérica do identificador de aviso. Por exemplo, se você desejar suprimir BC42024, o aviso para variáveis locais não utilizados, especificar `/nowarn:42024`.  
  
 Para obter mais informações sobre os números de identificação de aviso, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Para definir /nowarn no Visual Studio ambiente de desenvolvimento integrado|  
|---|  
|1.  Tenha um projeto selecionado no **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique na guia **Compilar**.<br />3.  Selecione o **desativar todos os avisos** caixa de seleção para desativar todos os avisos.<br />     - ou -<br />     Para desativar um aviso específico, clique em **nenhum** da lista suspensa adjacente para o aviso.|  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` e não exibe avisos.  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` e não exibe os avisos para variáveis locais não utilizadas (42024).  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)
