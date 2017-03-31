---
title: "-keycontainer (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /keycontainer
dev_langs:
- CSharp
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 723ee5ee49b1a912bf06369f68f8702ca38848a1
ms.lasthandoff: 03/13/2017

---
# <a name="keycontainer-c-compiler-options"></a>/keycontainer (opções do compilador C#)
Especifica o nome do contêiner da chave de criptografia.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/keycontainer:string  
```  
  
## <a name="arguments"></a>Arguments  
 `string`  
 O nome do contêiner de chave de nome forte.  
  
## <a name="remarks"></a>Comentários  
 Quando a opção **/keycontainer** é usada, o compilador cria um componente compartilhável inserindo uma chave pública do contêiner especificado no manifesto do assembly e assinando o assembly definitivo com a chave privada. Para gerar um arquivo de chave, digite sn -k `file` na linha de comando. O sn -i instala o par de chaves no contêiner.  
  
 Se você compilar com [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), o nome do arquivo de chave será mantido no módulo e incorporado no assembly quando você compilar esse módulo em um assembly com [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Também é possível especificar essa opção como um atributo personalizado (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>) no código-fonte para qualquer módulo MSIL (Microsoft Intermediate Language).  
  
 Também é possível passar suas informações de criptografia para o compilador com [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md). Use [/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) se você quiser a chave pública adicionada ao manifesto do assembly, mas deseja atrasar a assinatura do assembly até que ela seja testada.  
  
 Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](https://msdn.microsoft.com/library/xwb8f617) e [Atraso na Assinatura de um Assembly](http://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Essa opção do compilador não está disponível no ambiente de desenvolvimento do Visual Studio.  
  
 É possível acessar de maneira programática essa opção do compilador com <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
