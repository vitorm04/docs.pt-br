---
title: "-codepage (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37f40312f1218b8e666eae7cb2de6c768ee32108
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
