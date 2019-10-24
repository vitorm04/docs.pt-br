---
title: /debug (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: 27485cda9bb2af980b300180134fd7e99ffceeba
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775681"
---
# <a name="-debug-visual-basic"></a>-debug (Visual Basic)

Faz com que o compilador gere informações de depuração e coloque-as nos arquivos de saída.

## <a name="syntax"></a>Sintaxe

```console
-debug[+ | -]
```

ou

```console
-debug:[full | pdbonly]
```

## <a name="arguments"></a>Arguments

|Termo|Definição|
|---|---|
|`+` &#124; `-`|Opcional. Especificar `+` ou `/debug` faz com que o compilador gere informações de depuração e coloque-as em um arquivo. pdb. A especificação de `-` tem o mesmo efeito que não especificar `/debug`.|
|`full` &#124; `pdbonly`|Opcional. Especifica o tipo de informações de depuração geradas pelo compilador. Se você não especificar `/debug:pdbonly`, o padrão será `full`, o que permite anexar um depurador ao programa em execução. O argumento `pdbonly` permite a depuração de código-fonte quando o programa é iniciado no depurador, mas exibe o código de linguagem de assembly somente quando o programa em execução está anexado ao depurador.|

## <a name="remarks"></a>Comentários

Use essa opção para criar builds de depuração. Se você não especificar `/debug`, `/debug+` ou `/debug:full`, não será possível depurar o arquivo de saída do programa.

Por padrão, as informações de depuração não são emitidas (`/debug-`). Para emitir informações de depuração, especifique `/debug` ou `/debug+`.

Para obter informações sobre como configurar o desempenho de depuração de um aplicativo, consulte [Facilitando a depuração de uma imagem](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).

|Para definir-depurar no ambiente de desenvolvimento integrado do Visual Studio|
|---|
|1. com um projeto selecionado em **Gerenciador de soluções**, no menu **projeto** , clique em **Propriedades**. <br />2. Clique na guia **Compilar** .<br />3. clique em **Opções de compilação avançadas**.<br />4. modifique o valor na caixa **gerar informações de depuração** .|

## <a name="example"></a>Exemplo

O exemplo a seguir coloca as informações de depuração no arquivo de saída `App.exe`.

```console
vbc -debug -out:app.exe test.vb
```

## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
