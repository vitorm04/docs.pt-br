---
title: "Configurando a validação de atividades"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 440f3ee85fe24707c6bb433736bf6104d9e0dfc5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-activity-validation"></a>Configurando a validação de atividades
Validação de atividade autores e permite que usuários da atividade para identificar e relatar erros na configuração de uma atividade antes da execução. [!INCLUDE[wf](../../../includes/wf-md.md)] fornece os seguintes tipos de validação de atividade:  
  
-   `RequiredArgument` e atributos de `OverloadGroup` .  
  
-   Validação classe base imperativa.  
  
-   Restrições declarativas.  
  
 `RequiredArgument` e atributos de `OverloadGroup` indicam que determinados argumentos em uma atividade são necessários. A validação classe base imperativa fornece uma maneira simples para uma atividade fornece validação sobre se, e restrições declarativas permitem a validação sobre a atividade e sua relação com o fluxo de trabalho contém. Se uma atividade não é configurado corretamente de acordo com os requisitos de validação, erros e avisos de validação são retornados. Se um trabalho de que são criados usando o designer de trabalho, todos os erros e avisos de validação são exibidos no designer. Se o trabalho são criados fora do designer de trabalho todos os erros de validação são retornados quando o fluxo de trabalho é chamado. Independentemente de como funciona foram criados, um trabalho com erros de validação são permitidos nunca executar. Esta seção fornece uma visão geral desses tipos de validação de atividade e como validação de atividade é chamada.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Argumentos necessários e grupos de sobrecarga](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)  
 Descreve como usar atributos de `RequiredArgument` e de `OverloadGroup` para fornecer validação.  
  
 [Validação baseada em código obrigatório](../../../docs/framework/windows-workflow-foundation/imperative-code-based-validation.md)  
 Descreve como usar a validação classe base para <xref:System.Activities.CodeActivity> e atividades com base <xref:System.Activities.NativeActivity> .  
  
 [Restrições declarativas](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)  
 Descreve como usar restrições declarativas para fornecer validação complexa de atividade.  
  
 [Invocando a validação de atividades](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)  
 Discute quando a validação de atividade é chamado automaticamente e como chamar explicitamente validação.  
  
## <a name="reference"></a>Referência  
  
## <a name="related-sections"></a>Seções relacionadas
