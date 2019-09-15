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
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="06126-102">Como: exibir erros de validação em um designer com hospedagem alterada</span><span class="sxs-lookup"><span data-stu-id="06126-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="06126-103">Este tópico descreve como recuperar e publicar erros de validação em [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]rehosted.</span><span class="sxs-lookup"><span data-stu-id="06126-103">This topic describes how to retrieve and publish validation errors in a rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="06126-104">Isso fornece-nos com um procedimento para confirmar que um fluxo de trabalho em um designer rehosted é válido.</span><span class="sxs-lookup"><span data-stu-id="06126-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="06126-105">Esta tarefa tem duas partes.</span><span class="sxs-lookup"><span data-stu-id="06126-105">This task has two parts.</span></span> <span data-ttu-id="06126-106">O primeiro é fornecer uma implementação <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span><span class="sxs-lookup"><span data-stu-id="06126-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="06126-107">Há um método importante para implementar essa interface, o <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> que o transmitirão uma lista de objetos <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> que contêm informações sobre os erros ao log de depuração.</span><span class="sxs-lookup"><span data-stu-id="06126-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="06126-108">Após implementado a interface, você recupera informações de erro publicar uma instância dessa implementação para o contexto de edição.</span><span class="sxs-lookup"><span data-stu-id="06126-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="06126-109">Implementar a interface de IValidationErrorService</span><span class="sxs-lookup"><span data-stu-id="06126-109">Implement the IValidationErrorService Interface</span></span>  
  
1. <span data-ttu-id="06126-110">Aqui está um exemplo de código para uma implementação simples que grava para fora os erros de validação para o log de depuração.</span><span class="sxs-lookup"><span data-stu-id="06126-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
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
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="06126-111">Publicação ao contexto de edição</span><span class="sxs-lookup"><span data-stu-id="06126-111">Publishing to the Editing Context</span></span>  
  
1. <span data-ttu-id="06126-112">Aqui está o código que irá publicar esse ao contexto de edição.</span><span class="sxs-lookup"><span data-stu-id="06126-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
