---
title: "Como Erros de validação de exibição em um designer de Rehosted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bbf6bcf6550c17a514edb28eecbe8d5d74ba7af2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="ebeb0-102">Como Erros de validação de exibição em um designer de Rehosted</span><span class="sxs-lookup"><span data-stu-id="ebeb0-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="ebeb0-103">Este tópico descreve como recuperar e publicar erros de validação em [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]rehosted.</span><span class="sxs-lookup"><span data-stu-id="ebeb0-103">This topic describes how to retrieve and publish validation errors in a rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="ebeb0-104">Isso fornece-nos com um procedimento para confirmar que um fluxo de trabalho em um designer rehosted é válido.</span><span class="sxs-lookup"><span data-stu-id="ebeb0-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="ebeb0-105">Esta tarefa tem duas partes.</span><span class="sxs-lookup"><span data-stu-id="ebeb0-105">This task has two parts.</span></span> <span data-ttu-id="ebeb0-106">O primeiro é fornecer uma implementação <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span><span class="sxs-lookup"><span data-stu-id="ebeb0-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="ebeb0-107">Há um método importante para implementar essa interface, o <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> que o transmitirão uma lista de objetos <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> que contêm informações sobre os erros ao log de depuração.</span><span class="sxs-lookup"><span data-stu-id="ebeb0-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="ebeb0-108">Após implementado a interface, você recupera informações de erro publicar uma instância dessa implementação para o contexto de edição.</span><span class="sxs-lookup"><span data-stu-id="ebeb0-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="ebeb0-109">Implementar a interface de IValidationErrorService</span><span class="sxs-lookup"><span data-stu-id="ebeb0-109">Implement the IValidationErrorService Interface</span></span>  
  
1.  <span data-ttu-id="ebeb0-110">Aqui está um exemplo de código para uma implementação simples que grava para fora os erros de validação para o log de depuração.</span><span class="sxs-lookup"><span data-stu-id="ebeb0-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
    ```  
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
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="ebeb0-111">Publicação ao contexto de edição</span><span class="sxs-lookup"><span data-stu-id="ebeb0-111">Publishing to the Editing Context</span></span>  
  
1.  <span data-ttu-id="ebeb0-112">Aqui está o código que irá publicar esse ao contexto de edição.</span><span class="sxs-lookup"><span data-stu-id="ebeb0-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
