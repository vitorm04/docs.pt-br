---
title: "/bugreport (Opções do Compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /bugreport
dev_langs:
- CSharp
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
caps.latest.revision: 20
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
ms.openlocfilehash: 17ec8f708485b52f82b797e90dc64f7d90914ad9
ms.lasthandoff: 03/13/2017

---
# <a name="bugreport-c-compiler-options"></a>/bugreport (opções do compilador C#)
Especifica que as informações de depuração devem ser colocadas em um arquivo para análise posterior.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 O nome do arquivo que conterá o relatório de bug.  
  
## <a name="remarks"></a>Comentários  
 A opção **/bugreport** especifica que as informações a seguir devem ser colocadas em `file`:  
  
-   Uma cópia de todos os arquivos de código-fonte na compilação.  
  
-   Uma lista das opção do compilador usadas na compilação.  
  
-   Informações de versão sobre o compilador, o tempo de execução e o sistema operacional.  
  
-   Assemblies e módulos referenciados, salvos como dígitos hexadecimais, exceto os assemblies que vêm com o .NET Framework e o SDK.  
  
-   Saída do compilador, se houver.  
  
-   Uma solicitação de descrição do problema.  
  
-   Uma solicitação de como você acha que o problema deve ser corrigido.  
  
 Se essa opção for usada com **/errorreport:prompt** ou **/errorreport:send**, as informações no arquivo serão enviadas à Microsoft Corporation.  
  
 Como uma cópia de todos os arquivos de código-fonte será colocada no `file`, talvez seja desejável reproduzir o suposto defeito do código no programa mais curto possível.  
  
 Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.  
  
 Observe que os conteúdos do arquivo gerado expõem o código-fonte, o que pode resultar na divulgação acidental de informações.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [/errorreport (Opções do Compilador do C#)](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
