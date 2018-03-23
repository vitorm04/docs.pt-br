---
title: -página de código (Visual Basic)
ms.date: 03/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 736b35f51657aa7b21a6a077d70f5e9ff0d4fb85
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-codepage-visual-basic"></a>-página de código (Visual Basic)
Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`id`|Necessário. O compilador usa a página de código especificada por `id` para interpretar a codificação dos arquivos de origem.|  
  
## <a name="remarks"></a>Comentários  
 Para compilar o código-fonte salvo com uma codificação específica, você pode usar `-codepage` para especificar a página de código deve ser usada. O `-codepage` opção se aplica a todos os arquivos de código-fonte na sua compilação. Para obter mais informações, consulte [codificação de caracteres no .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).  
  
 O `-codepage` opção não é necessária se os arquivos de código-fonte foram salvos com a página de código ANSI atual, Unicode ou UTF-8 com uma assinatura. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] salva todos os arquivos de código-fonte com a página de código ANSI atual por padrão, a menos que o usuário especifique outra codificação no **codificação** caixa de diálogo. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] usa o **codificação** caixa de diálogo para abrir arquivos de código-fonte salvos com uma página de código diferente.  
  
> [!NOTE]
>  O `-codepage` opção não está disponível de dentro do [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] ambiente de desenvolvimento; está disponível somente quando estiver compilando na linha de comando.  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
