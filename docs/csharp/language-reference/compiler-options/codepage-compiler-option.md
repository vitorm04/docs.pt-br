---
title: "-codepage (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /codepage
dev_langs:
- CSharp
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: 15
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b80f6fcf8891d2f0b921af01cc094f624d807aa1
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="codepage-c-compiler-options"></a>/codepage (opções do compilador C#)
Esta opção especifica qual página de código deve ser usada durante a compilação caso a página necessária não seja a página de código padrão atual do sistema.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
 `id`  
 Especifica a ID da página de código a ser usada para todos os arquivos de código-fonte na compilação.  
  
## <a name="remarks"></a>Comentários  
 Se um ou mais arquivos de código-fonte que não foram criados para usar a página de código padrão no computador forem compilados, será possível usar a opção **/codepage** para especificar qual página de código deve ser usada. **/codepage** se aplica a todos os arquivos de código-fonte na compilação.  
  
 Caso os arquivos de código-fonte tiverem sido criados com a mesma página de código em uso no computador, com UNICODE ou UTF-8, não será necessário usar **/codepage**.  
  
 Consulte [GetCPInfo](http://go.microsoft.com/fwlink/?LinkId=148371) para obter informações sobre como localizar quais páginas de código têm suporte do sistema.  
  
 Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)

