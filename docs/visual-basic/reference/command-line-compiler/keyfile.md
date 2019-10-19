---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 84b291a28cd4e253f44063258894aa672904d15b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581990"
---
# <a name="-keyfile"></a>-keyfile

Especifica um arquivo que contém uma chave ou um par de chaves para fornecer um nome forte ao assembly.

## <a name="syntax"></a>Sintaxe

```console
-keyfile:file
```

## <a name="arguments"></a>Arguments

`file`  
Necessário. Arquivo que contém a chave. Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").

## <a name="remarks"></a>Comentários

O compilador insere a chave pública no manifesto do assembly e, em seguida, assina o assembly final com a chave privada. Para gerar um arquivo de chave, digite `sn -k file` na linha de comando. Para obter mais informações, consulte [sn. exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).

Se você compilar com `-target:module`, o nome do arquivo de chave será mantido no módulo e incorporado ao assembly que é criado quando você compila um assembly com [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).

Também é possível passar suas informações de criptografia para o compilador com [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) se quiser um assembly parcialmente assinado.

Você também pode especificar essa opção como um atributo personalizado (<xref:System.Reflection.AssemblyKeyFileAttribute>) no código-fonte para qualquer módulo de linguagem intermediária da Microsoft.

Caso ambos `-keyfile` e [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) sejam especificados (por opção de linha de comando ou por atributo personalizado) na mesma compilação, o compilador primeiro tenta o contêiner de chave. Se isso ocorrer, o assembly será assinado com as informações no contêiner de chaves. Se o compilador não encontrar o contêiner de chave, ele tentará o arquivo especificado com `-keyfile`. Se isso for bem sucedido, o assembly será assinado com as informações no arquivo de chave e as informações de chave serão instaladas no contêiner de chave (semelhante a `sn -i`) para que, na próxima compilação, o contêiner de chave seja válido.

Observe que um arquivo de chave pode conter somente a chave pública.

Consulte [criando e usando assemblies de nome forte](../../../standard/assembly/create-use-strong-named.md) para obter mais informações sobre como assinar um assembly.

> [!NOTE]
> A opção `-keyfile` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.

## <a name="example"></a>Exemplo

O código a seguir compila o arquivo de origem `Input.vb` e especifica um arquivo de chave.

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a>Consulte também

- [Assemblies no .NET](../../../standard/assembly/index.md)
- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-referência (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
