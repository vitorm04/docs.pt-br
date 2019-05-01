---
title: Usando o ExpressionTextBox em um designer personalizado de atividades
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: c85254f1ae7ba8a269568cf1a14acf367b595e33
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004751"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="3b342-102">Usando o ExpressionTextBox em um designer personalizado de atividades</span><span class="sxs-lookup"><span data-stu-id="3b342-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="3b342-103">Este exemplo mostra como usar <xref:System.Activities.Presentation.View.ExpressionTextBox> em um designer personalizado de atividade.</span><span class="sxs-lookup"><span data-stu-id="3b342-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="3b342-104">A atividade personalizado, `MultiAssign`, atribui dois valores de cadeia de caracteres a duas variáveis de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3b342-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="3b342-105">Alguns controles de <xref:System.Activities.Presentation.View.ExpressionTextBox> associação a <xref:System.Activities.InArgument>s e associar a qualquer <xref:System.Activities.OutArgument>S.</span><span class="sxs-lookup"><span data-stu-id="3b342-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="3b342-106">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="3b342-106">Sample details</span></span>
 <span data-ttu-id="3b342-107">`ArgumentToExpressionConverter` é o conversor de tipo usado para associar expressões para argumentos.</span><span class="sxs-lookup"><span data-stu-id="3b342-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="3b342-108">`ConverterParameter` deve ser definido como `In` ou a `Out` como apropriado.</span><span class="sxs-lookup"><span data-stu-id="3b342-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="3b342-109">`InOut` não é suportado.</span><span class="sxs-lookup"><span data-stu-id="3b342-109">`InOut` is not supported.</span></span>

 <span data-ttu-id="3b342-110">O `UseLocationExpression` atributo é usado em `OutArgument`s para especificar que a expressão deve ser uma expressão de L-value ("esquerdo valor" ou "valor local").</span><span class="sxs-lookup"><span data-stu-id="3b342-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="3b342-111">Na maioria dos casos, uma expressão de L- valor é um identificador válido Visual Basic usado para indicar que `OutArgument` que está sendo retornado é uma variável ou um nome de argumento.</span><span class="sxs-lookup"><span data-stu-id="3b342-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="3b342-112">O atributo de `MaxLines` é definido como um nesse exemplo e `MinLines` não está definido.</span><span class="sxs-lookup"><span data-stu-id="3b342-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="3b342-113">Isso indica que <xref:System.Activities.Presentation.View.ExpressionTextBox> é um tamanho fixo de uma linha independentemente da quantidade de texto digitado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="3b342-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="3b342-114">Para permitir que <xref:System.Activities.Presentation.View.ExpressionTextBox> venha a entrada do usuário apta, defina `MaxLines` maior do que `MinLines`.</span><span class="sxs-lookup"><span data-stu-id="3b342-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="3b342-115">Um ExpressionTextBox só pode ser associado para argumentos, e não pode ser associado para propriedades de CLR.</span><span class="sxs-lookup"><span data-stu-id="3b342-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="3b342-116">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="3b342-116">To use this sample</span></span>

1. <span data-ttu-id="3b342-117">Usando o Visual Studio 2010, abra o arquivo de Expressiontextboxsample.</span><span class="sxs-lookup"><span data-stu-id="3b342-117">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="3b342-118">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="3b342-118">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="3b342-119">Para executar este exemplo</span><span class="sxs-lookup"><span data-stu-id="3b342-119">To run this sample</span></span>

1. <span data-ttu-id="3b342-120">Adicione um novo aplicativo de console do fluxo de trabalho à solução.</span><span class="sxs-lookup"><span data-stu-id="3b342-120">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="3b342-121">Adicione uma referência para o **ExpressionTextBoxSample** projeto do novo projeto de aplicativo de Console do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3b342-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="3b342-122">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="3b342-122">Build the solution.</span></span>

4. <span data-ttu-id="3b342-123">Arraste o **MultiAssign** atividade da caixa de ferramentas e solte-o no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3b342-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="3b342-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3b342-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3b342-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3b342-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3b342-126">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="3b342-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3b342-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3b342-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="3b342-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b342-128">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="3b342-129">Desenvolvendo aplicativos com o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="3b342-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
