---
title: /quiet | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /quiet
- quiet
dev_langs:
- VB
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: feafed7464248c38ec70087795a28ead8b8793f3
ms.lasthandoff: 03/13/2017

---
# <a name="quiet"></a>/quiet
Impede que o compilador de mostrar código para erros relacionados à sintaxe e avisos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/quiet  
```  
  
## <a name="remarks"></a>Comentários  
 Por padrão, `/quiet` não está em vigor. Quando o compilador reporta um erro de sintaxe ou aviso, ele também produz a linha do código-fonte. Para aplicações que analisam a saída do compilador, pode ser mais conveniente para o compilador apenas o texto do diagnóstico de saída.  
  
 No exemplo a seguir, `Module1` gera um erro que inclui código-fonte quando compilado sem `/quiet`.  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 Saída:  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 Compilado com `/quiet`, o compilador gera o seguinte:  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  O `/quiet` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` e não mostra código para diagnósticos de compilador relacionados com a sintaxe:  
  
```  
vbc /quiet t2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
