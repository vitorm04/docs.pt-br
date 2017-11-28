---
title: "-keycontainer (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0292ff38b1d03f5960a20858fbb9c42a6aff1f43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="keycontainer-c-compiler-options"></a>/keycontainer (opções do compilador C#)
Especifica o nome do contêiner da chave de criptografia.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/keycontainer:string  
```  
  
## <a name="arguments"></a>Arguments  
 `string`  
 O nome do contêiner de chave de nome forte.  
  
## <a name="remarks"></a>Comentários  
 Quando a opção **/keycontainer** é usada, o compilador cria um componente compartilhável inserindo uma chave pública do contêiner especificado no manifesto do assembly e assinando o assembly definitivo com a chave privada. Para gerar um arquivo de chave, digite sn -k `file` na linha de comando. O sn -i instala o par de chaves no contêiner.  
  
 Se você compilar com [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), o nome do arquivo de chave será mantido no módulo e incorporado no assembly quando você compilar esse módulo em um assembly com [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Também é possível especificar essa opção como um atributo personalizado (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) no código-fonte de qualquer módulo MSIL (Microsoft Intermediate Language).  
  
 Também é possível passar suas informações de criptografia para o compilador com [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md). Use [/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) se você quiser a chave pública adicionada ao manifesto do assembly, mas deseja atrasar a assinatura do assembly até que ela seja testada.  
  
 Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) e [Atraso na Assinatura de um Assembly](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Essa opção do compilador não está disponível no ambiente de desenvolvimento do Visual Studio.  
  
 Você pode acessar programaticamente essa opção do compilador com <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
