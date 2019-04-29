---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: 51cfe4a52af2fbcd51a4f9e2dc738e83fe0852c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793972"
---
# <a name="-keycontainer"></a>-keycontainer
Especifica um nome de contêiner de chave para um par de chaves dar um nome forte de um assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`container`|Necessário. Arquivo de contêiner que contém a chave. Coloque o nome do arquivo entre aspas ("") se o nome contiver um espaço.|  
  
## <a name="remarks"></a>Comentários  
 O compilador cria o componente compartilhável inserindo uma chave pública no manifesto do assembly e assinando o assembly final com a chave privada. Para gerar um arquivo de chave, digite `sn -k file` na linha de comando. O `-i` opção instala o par de chaves no contêiner. Para obter mais informações, consulte [Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Se você compilar com `-target:module`, o nome do arquivo de chave será mantido no módulo e incorporado no assembly que é criado quando você compila um assembly com [- addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Também é possível especificar essa opção como um atributo personalizado (<xref:System.Reflection.AssemblyKeyNameAttribute>) no código-fonte de qualquer módulo MSIL (Microsoft Intermediate Language).  
  
 Também é possível passar suas informações de criptografia para o compilador com [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md). Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) se quiser um assembly parcialmente assinado.  
  
 Ver [criando e usando Assemblies nomes fortes](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) para obter mais informações sobre como assinar um assembly.  
  
> [!NOTE]
>  O `-keycontainer` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila o arquivo de origem `Input.vb` e especifica um contêiner de chave.  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Assemblies no .NET](../../../standard/assembly/index.md)
- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
