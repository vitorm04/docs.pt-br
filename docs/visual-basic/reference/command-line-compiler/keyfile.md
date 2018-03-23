---
title: -keyfile
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02169f1f43ba93b68dc47f5bad038b78d3635a80
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-keyfile"></a>-keyfile
Especifica um arquivo que contém uma chave ou par de chaves para dar um nome forte de um assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Necessário. Arquivo que contém a chave. Se o nome do arquivo contém um espaço, coloque o nome entre aspas ("").  
  
## <a name="remarks"></a>Comentários  
 O compilador insere a chave pública no manifesto do assembly e, em seguida, assina o assembly final com a chave privada. Para gerar um arquivo de chave, digite `sn -k file` na linha de comando. Para obter mais informações, consulte [Sn.exe (ferramenta de nome forte)][Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Se você compilar com `-target:module`, o nome do arquivo da chave é mantido no módulo e incorporado no assembly, que é criado quando você compila um assembly com [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Também é possível passar suas informações de criptografia para o compilador com [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) se quiser um assembly parcialmente assinado.  
  
 Você também pode especificar esta opção como um atributo personalizado (<xref:System.Reflection.AssemblyKeyFileAttribute>) no código-fonte para qualquer módulo de linguagem intermediária da Microsoft.  
  
 Em caso de ambos `-keyfile` e [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) são especificado (pela opção de linha de comando ou pelo atributo personalizado) na mesma compilação, o compilador tenta primeiro o contêiner de chave. Se isso ocorrer, o assembly será assinado com as informações no contêiner de chaves. Se o compilador não localizar o contêiner de chave, ele tenta o arquivo especificado com `-keyfile`. Se isso for bem-sucedida, o assembly é assinado com as informações no arquivo de chave e as informações de chave são instaladas no contêiner de chave (semelhante ao `sn -i`) para que na próxima compilação, o contêiner de chave será válido.  
  
 Observe que um arquivo de chave pode conter somente a chave pública.  
  
 Consulte [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) para obter mais informações sobre como assinar um assembly.  
  
> [!NOTE]
>  O `-keyfile` opção não está disponível de dentro do [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] ambiente de desenvolvimento; está disponível somente quando estiver compilando na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila o arquivo de origem `Input.vb` e especifica um arquivo de chave.  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-referência (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
