---
title: /keycontainer | Documentos do Microsoft
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
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
caps.latest.revision: 16
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
ms.openlocfilehash: 68fa09edce5c0c9af143197f9379d5a46afab52e
ms.lasthandoff: 03/13/2017

---
# <a name="keycontainer"></a>/keycontainer
Especifica um nome de contêiner de chave para um par de chaves dar um nome forte de um assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/keycontainer:container  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`container`|Necessário. Arquivo de contêiner que contém a chave. Coloque o nome do arquivo entre aspas ("") se o nome contém um espaço.|  
  
## <a name="remarks"></a>Comentários  
 O compilador cria o componente compartilhável inserindo uma chave pública no manifesto do assembly e assinando o assembly final com a chave privada. Para gerar um arquivo de chave, digite `sn -k``file` na linha de comando. O `-i` opção instala o par de chaves no contêiner. Para saber mais, veja [Sn.exe (Ferramenta de Nome Forte)](https://msdn.microsoft.com/library/k5b5tt23).  
  
 Se você compilar com `/target:module`, o nome do arquivo da chave é mantido no módulo e incorporado no assembly, que é criado quando você compila um assembly com [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Você também pode especificar esta opção como um atributo personalizado (<xref:System.Reflection.AssemblyKeyNameAttribute>) no código-fonte para qualquer módulo do Microsoft intermediate language (MSIL).</xref:System.Reflection.AssemblyKeyNameAttribute>  
  
 Você também pode passar suas informações de criptografia para o compilador com [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md). Use [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) se você quiser um assembly parcialmente assinado.  
  
 Consulte [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) para obter mais informações sobre como assinar um assembly.  
  
> [!NOTE]
>  O `/keycontainer` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila o arquivo de origem `Input.vb` e especifica um contêiner de chave.  
  
```  
vbc /keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
