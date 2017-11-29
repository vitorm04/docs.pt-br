---
title: /moduleassemblyname
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d9a5307970ac745b4f102d0008e64b985c00e52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="moduleassemblyname"></a>/moduleassemblyname
Especifica o nome do assembly do qual esse módulo fará parte.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`assembly_name`|O nome do assembly que este módulo fará parte do.|  
  
## <a name="remarks"></a>Comentários  
 O compilador processa o `/moduleassemblyname` se única opção de `/target:module` opção foi especificada. Isso faz com que o compilador criar um módulo. O módulo criado pelo compilador é válido somente para o conjunto especificado com o `/moduleassemblyname` opção. Se você colocar o módulo em um assembly diferente, ocorrerão erros de tempo de execução.  
  
 O `/moduleassemblyname` opção é necessária somente quando os seguintes condições forem verdadeiras:  
  
-   Um tipo de dados no módulo precisa acessar um `Friend` tipo em um assembly referenciado.  
  
-   O assembly referenciado concedeu acesso de assembly friend ao assembly no qual o módulo será criado.  
  
 Para obter mais informações sobre como criar um módulo, consulte [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Para obter mais informações sobre assemblies amigáveis, consulte [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
> [!NOTE]
>  O `/moduleassemblyname` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível apenas quando você compila a partir de um prompt de comando.  
  
## <a name="see-also"></a>Consulte também  
 [Como Compilar um Assembly de Vários Arquivos](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [/main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Assemblies Amigáveis](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)
