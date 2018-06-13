---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: e67fe05507c8cb3edd7f46cad19211ba11e3b054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652390"
---
# <a name="-quiet"></a>-quiet
Impede que o compilador de mostrar código para avisos e erros de sintaxe.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-quiet  
```  
  
## <a name="remarks"></a>Comentários  
 Por padrão, `-quiet` não está em vigor. Quando o compilador reporta um erro de sintaxe ou aviso, ele também produz a linha do código-fonte. Para aplicativos que analisar a saída do compilador, pode ser mais conveniente para o compilador somente o texto do diagnóstico de saída.  
  
 No exemplo a seguir, `Module1` gera um erro que inclui o código-fonte quando compilado sem `-quiet`.  
  
```vb  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 Saída:  
 
```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
``` 
 Compilado com `-quiet`, o compilador gera o seguinte:  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  O `-quiet` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e não mostra código para diagnósticos de compilador relacionados com a sintaxe:  
  
```  
vbc -quiet t2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
