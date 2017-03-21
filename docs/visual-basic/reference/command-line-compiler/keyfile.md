---
title: /keyfile | Documentos do Microsoft
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
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: 17
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
ms.openlocfilehash: c36eac96ac6302db0b567e8249af726c807c2c6c
ms.lasthandoff: 03/13/2017

---
# <a name="keyfile"></a>/keyfile
Especifica um arquivo que contém uma chave ou par de chaves para dar um nome forte de um assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Necessário. Arquivo que contém a chave. Se o nome do arquivo contém um espaço, coloque o nome entre aspas ("").  
  
## <a name="remarks"></a>Comentários  
 O compilador insere a chave pública no manifesto do assembly e, em seguida, assina o assembly final com a chave privada. Para gerar um arquivo de chave, digite `sn -k file` na linha de comando. Para saber mais, veja [Sn.exe (Ferramenta de Nome Forte)](https://msdn.microsoft.com/library/k5b5tt23).  
  
 Se você compilar com `/target:module`, o nome do arquivo da chave é mantido no módulo e incorporado no assembly, que é criado quando você compila um assembly com [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Você também pode passar suas informações de criptografia para o compilador com [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Use [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) se você quiser um assembly parcialmente assinado.  
  
 Você também pode especificar esta opção como um atributo personalizado (<xref:System.Reflection.AssemblyKeyFileAttribute>) no código-fonte para qualquer módulo de linguagem intermediária da Microsoft.</xref:System.Reflection.AssemblyKeyFileAttribute>  
  
 No caso de ambos `/keyfile` e [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) são especificados (pela opção de linha de comando ou pelo atributo personalizado) na mesma compilação, o compilador tenta primeiro o contêiner de chave. Se isso ocorrer, o assembly é assinado com as informações no contêiner de chave. Se o compilador não localizar o contêiner de chave, ele tentará o arquivo especificado com `/keyfile`. Se isso for bem-sucedida, o assembly é assinado com as informações no arquivo de chave e as informações de chave são instaladas no contêiner de chave (como `sn -i`) para que na próxima compilação, o contêiner de chave será válido.  
  
 Observe que um arquivo de chave pode conter somente a chave pública.  
  
 Consulte [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) para obter mais informações sobre como assinar um assembly.  
  
> [!NOTE]
>  O `/keyfile` opção não está disponível de dentro do [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] ambiente de desenvolvimento; está disponível apenas quando se compila da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila o arquivo de origem `Input.vb` e especifica um arquivo de chave.  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
