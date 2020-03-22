---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: cffc3c5f0ff3dd48ca2c74bde346a967b209dc5f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266736"
---
# <a name="-keyfile"></a>-keyfile
Especifica um arquivo contendo uma chave ou um par de tecla para dar a um conjunto um nome forte.  
  
## <a name="syntax"></a>Sintaxe  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a>Argumentos  
 `file`  
 Obrigatórios. Arquivo que contém a chave. Se o nome do arquivo contiver um espaço, feche o nome entre aspas (" ").  
  
## <a name="remarks"></a>Comentários  
 O compilador insere a chave pública no manifesto de montagem e, em seguida, assina a montagem final com a chave privada. Para gerar um arquivo de chave, digite `sn -k file` na linha de comando. Para obter mais informações, consulte [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Se você compilar com `-target:module`, o nome do arquivo-chave é mantido no módulo e incorporado no conjunto que é criado quando você compila um conjunto com [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Também é possível passar suas informações de criptografia para o compilador com [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) se quiser um assembly parcialmente assinado.  
  
 Você também pode especificar essa<xref:System.Reflection.AssemblyKeyFileAttribute>opção como um atributo personalizado ( ) no código-fonte de qualquer módulo de idioma intermediário da Microsoft.  
  
 No caso `-keyfile` de ambos e [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) serem especificados (seja por opção de linha de comando ou por atributo personalizado) na mesma compilação, o compilador primeiro tenta o contêiner de chaves. Se isso ocorrer, o assembly será assinado com as informações no contêiner de chaves. Se o compilador não encontrar o recipiente de chave, `-keyfile`ele tentará o arquivo especificado com . Se isso for bem sucedido, o conjunto é assinado com as informações no arquivo-chave, `sn -i`e as informações-chave são instaladas no recipiente de chave (semelhante a ) para que na próxima compilação, o recipiente de chave seja válido.  
  
 Observe que um arquivo de chave pode conter somente a chave pública.  
  
 Consulte [Criando e Usando Assembléias com Named Forte](../../../standard/assembly/create-use-strong-named.md) para obter mais informações sobre como assinar uma assembléia.  
  
> [!NOTE]
> A `-keyfile` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele só está disponível quando compilado a partir da linha de comando.

## <a name="example"></a>Exemplo

O código a seguir `Input.vb` compila o arquivo fonte e especifica um arquivo-chave.

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a>Confira também

- [Assemblies no .NET](../../../standard/assembly/index.md)
- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-referência (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
