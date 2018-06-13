---
title: Configurando a validação de atividades
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: e6fa043e0a0a96875319d556c19ab8ee90cd2139
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512594"
---
# <a name="configuring-activity-validation"></a>Configurando a validação de atividades
Validação de atividade autores e permite que usuários da atividade para identificar e relatar erros na configuração de uma atividade antes da execução. Windows Workflow Foundation (WF) fornece os seguintes três tipos de validação de atividades:  
  
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
