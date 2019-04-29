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
ms.openlocfilehash: a22773e2e37eb60ab6f1e88305266f41764311e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788837"
---
# <a name="-quiet"></a>-quiet

Impede que o compilador exibindo o código para avisos e erros de sintaxe.

## <a name="syntax"></a>Sintaxe

```
-quiet
```

## <a name="remarks"></a>Comentários

Por padrão, `-quiet` não está em vigor. Quando o compilador relatará um erro de sintaxe ou aviso, ele também produz a linha do código-fonte. Para aplicativos que analisar a saída do compilador, pode ser mais conveniente para o compilador gerar apenas o texto do diagnóstico.

No exemplo a seguir `Module1` gera um erro que inclui código-fonte quando compilado sem `-quiet`.

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

Compilado com `-quiet`, o compilador gera apenas o seguinte:

```
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> O `-quiet` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.

## <a name="example"></a>Exemplo

O seguinte código compila `T2.vb` e não exibe o código para o diagnóstico de compilador relacionados com a sintaxe:

```
vbc -quiet t2.vb
```

## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
