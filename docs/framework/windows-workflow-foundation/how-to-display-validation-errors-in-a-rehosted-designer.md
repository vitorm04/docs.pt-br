---
title: 'Como: exibir erros de validação em um designer com hospedagem alterada'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: 608868882f4bec23c03f0ec78f65673e76056030
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989659"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Como: exibir erros de validação em um designer com hospedagem alterada
Este tópico descreve como recuperar e publicar erros de validação em [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]rehosted. Isso fornece-nos com um procedimento para confirmar que um fluxo de trabalho em um designer rehosted é válido.  
  
 Esta tarefa tem duas partes. O primeiro é fornecer uma implementação <xref:System.Activities.Presentation.Validation.IValidationErrorService>.  Há um método importante para implementar essa interface, o <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> que o transmitirão uma lista de objetos <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> que contêm informações sobre os erros ao log de depuração.  Após implementado a interface, você recupera informações de erro publicar uma instância dessa implementação para o contexto de edição.  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a>Implementar a interface de IValidationErrorService  
  
1. Aqui está um exemplo de código para uma implementação simples que grava para fora os erros de validação para o log de depuração.  
  
    ```csharp  
    using System.Activities.Presentation.Validation;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Linq;  
  
    namespace VariableFinderShell  
    {  
        class DebugValidationErrorService : IValidationErrorService  
        {  
            public void ShowValidationErrors(IList<ValidationErrorInfo> errors)  
            {  
                errors.ToList().ForEach(vei => Debug.WriteLine(string.Format("Error: {0} ", vei.Message)));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a>Publicação ao contexto de edição  
  
1. Aqui está o código que irá publicar esse ao contexto de edição.  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
