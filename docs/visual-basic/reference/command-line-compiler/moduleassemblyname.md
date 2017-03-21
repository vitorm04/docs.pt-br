---
title: /moduleassemblyname | Documentos do Microsoft
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
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: 16
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
ms.openlocfilehash: f6b042b26ad866f177158562653c91f4f7527c04
ms.lasthandoff: 03/13/2017

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
|`assembly_name`|O nome do assembly que este módulo será uma parte.|  
  
## <a name="remarks"></a>Comentários  
 O compilador processa o `/moduleassemblyname` somente se opção o `/target:module` opção foi especificada. Isso faz com que o compilador crie um módulo. O módulo criado pelo compilador é válido somente para o conjunto especificado com o `/moduleassemblyname` opção. Se você colocar o módulo em um conjunto diferente, ocorrerão erros de tempo de execução.  
  
 O `/moduleassemblyname` opção é necessária somente quando as seguintes condições forem verdadeiras:  
  
-   Um tipo de dados no módulo precisa acessar um `Friend` tipo em um assembly referenciado.  
  
-   O assembly referenciado concedeu acesso assembly autorizado ao assembly no qual o módulo será criado.  
  
 Para obter mais informações sobre como criar um módulo, consulte [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Para obter mais informações sobre assemblies amigáveis, consulte [Assemblies amigáveis](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
> [!NOTE]
>  O `/moduleassemblyname` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando você compila a partir de um prompt de comando.  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar um Assembly de vários arquivos](http://msdn.microsoft.com/library/261c5583-8a76-412d-bda7-9b8ee3b131e5)   
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [/Main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)   
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Assemblies Amigáveis](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)
