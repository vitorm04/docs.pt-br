---
title: Atividades de expressão regular
ms.date: 03/30/2017
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
ms.openlocfilehash: 50daa5b6d7baab37f372de4c30c2e0d12b4fa943
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668945"
---
# <a name="regular-expression-activities"></a><span data-ttu-id="9718a-102">Atividades de expressão regular</span><span class="sxs-lookup"><span data-stu-id="9718a-102">Regular Expression Activities</span></span>
<span data-ttu-id="9718a-103">Este exemplo demonstra como criar um conjunto de atividades que expõe a funcionalidade de expressões regulares do <xref:System.Text.RegularExpressions> .</span><span class="sxs-lookup"><span data-stu-id="9718a-103">This sample demonstrates how to create a set of activities that expose the regular expression functionality of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="9718a-104">Essas atividades personalizados podem ser usadas em um aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9718a-104">These custom activities can be used within a workflow application.</span></span> <span data-ttu-id="9718a-105">Para obter mais informações sobre expressões regulares, consulte [RegularExpressions](https://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span><span class="sxs-lookup"><span data-stu-id="9718a-105">For more information about regular expressions, see [N:System.Text.RegularExpressions](https://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span></span>  
  
 <span data-ttu-id="9718a-106">A tabela a seguir detalha as atividades personalizados nesse exemplo.</span><span class="sxs-lookup"><span data-stu-id="9718a-106">The following table details the custom activities in this sample.</span></span>  
  
|<span data-ttu-id="9718a-107">Atividade</span><span class="sxs-lookup"><span data-stu-id="9718a-107">Activity</span></span>|<span data-ttu-id="9718a-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="9718a-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="9718a-109">IsMatch</span><span class="sxs-lookup"><span data-stu-id="9718a-109">IsMatch</span></span>|<span data-ttu-id="9718a-110">Especifica se a expressão regular encontrado uma correspondência na cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="9718a-110">Specifies whether the regular expression found a match in the input string.</span></span>|  
|<span data-ttu-id="9718a-111">Correspondências</span><span class="sxs-lookup"><span data-stu-id="9718a-111">Matches</span></span>|<span data-ttu-id="9718a-112">Procura uma cadeia de caracteres de entrada por todas as ocorrências de uma expressão regular e retorna todas as correspondências com êxito.</span><span class="sxs-lookup"><span data-stu-id="9718a-112">Searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span>|  
|<span data-ttu-id="9718a-113">Substituir</span><span class="sxs-lookup"><span data-stu-id="9718a-113">Replace</span></span>|<span data-ttu-id="9718a-114">Dentro de uma cadeia de caracteres especificada de entrada, substitui as cadeias de caracteres que correspondem um padrão de expressão regular com uma cadeia de caracteres especificada de substituição.</span><span class="sxs-lookup"><span data-stu-id="9718a-114">Within a specified input string, replaces strings that match a regular expression pattern with a specified replacement string.</span></span>|  
  
## <a name="ismatch"></a><span data-ttu-id="9718a-115">IsMatch</span><span class="sxs-lookup"><span data-stu-id="9718a-115">IsMatch</span></span>  
 <span data-ttu-id="9718a-116">A atividade personalizado de `IsMatch` retorna `true` se a propriedade de cadeia de caracteres de `Input` encontra uma correspondência na expressão regular especificada na propriedade de `Pattern` .</span><span class="sxs-lookup"><span data-stu-id="9718a-116">The `IsMatch` custom activity returns `true` if the `Input` string property finds a match in the regular expression specified in the `Pattern` property.</span></span> <span data-ttu-id="9718a-117">A atividade deriva de <xref:System.Activities.CodeActivity%601> e dentro de <xref:System.Activities.CodeActivity%601.Execute%2A> o método chama o método de <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> .</span><span class="sxs-lookup"><span data-stu-id="9718a-117">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method.</span></span>  
  
 <span data-ttu-id="9718a-118">A tabela a seguir descreve as propriedades e o valor de retorno para atividades personalizado de `IsMatch` .</span><span class="sxs-lookup"><span data-stu-id="9718a-118">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="9718a-119">Propriedade ou valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9718a-119">Property or Return Value</span></span>|<span data-ttu-id="9718a-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="9718a-120">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="9718a-121">Padrão (necessário)</span><span class="sxs-lookup"><span data-stu-id="9718a-121">Pattern (required)</span></span>|<span data-ttu-id="9718a-122">A expressão regular com a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="9718a-122">The regular expression to search with.</span></span>|  
|<span data-ttu-id="9718a-123">Entrada (necessária)</span><span class="sxs-lookup"><span data-stu-id="9718a-123">Input (required)</span></span>|<span data-ttu-id="9718a-124">A cadeia de caracteres de entrada para procurar.</span><span class="sxs-lookup"><span data-stu-id="9718a-124">The input string to search.</span></span>|  
|<span data-ttu-id="9718a-125">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="9718a-125">RegexOptions</span></span>|<span data-ttu-id="9718a-126">Combinação OR bit a bit de [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="9718a-126">Bitwise OR combination of [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="9718a-127">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9718a-127">Return value</span></span>|<span data-ttu-id="9718a-128">`true` se a entrada encontra uma correspondência no padrão fornecido; se não `false`.</span><span class="sxs-lookup"><span data-stu-id="9718a-128">`true` if the input finds a match in the provided pattern; otherwise `false`.</span></span>|  
  
 <span data-ttu-id="9718a-129">O exemplo de código demonstra como usar a atividade personalizado de `IsMatch` .</span><span class="sxs-lookup"><span data-stu-id="9718a-129">The following code example demonstrates how to use the `IsMatch` custom activity.</span></span>  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a><span data-ttu-id="9718a-130">Correspondências</span><span class="sxs-lookup"><span data-stu-id="9718a-130">Matches</span></span>  
 <span data-ttu-id="9718a-131">A atividade personalizado de `Matches` procura uma cadeia de caracteres de entrada por todas as ocorrências de uma expressão regular e retorna todas as correspondências com êxito.</span><span class="sxs-lookup"><span data-stu-id="9718a-131">The `Matches` custom activity searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span> <span data-ttu-id="9718a-132">A atividade deriva de <xref:System.Activities.CodeActivity%601> e dentro de <xref:System.Activities.CodeActivity%601.Execute%2A> o método chama o método de <xref:System.Text.RegularExpressions.Regex.Matches%2A> .</span><span class="sxs-lookup"><span data-stu-id="9718a-132">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Matches%2A> method.</span></span>  
  
 <span data-ttu-id="9718a-133">A tabela a seguir descreve as propriedades e o valor de retorno para atividades personalizado de `IsMatch` .</span><span class="sxs-lookup"><span data-stu-id="9718a-133">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="9718a-134">Propriedade ou valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9718a-134">Property or Return Value</span></span>|<span data-ttu-id="9718a-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="9718a-135">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="9718a-136">Padrão (necessário)</span><span class="sxs-lookup"><span data-stu-id="9718a-136">Pattern (required)</span></span>|<span data-ttu-id="9718a-137">A expressão regular com a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="9718a-137">The regular expression to search with.</span></span>|  
|<span data-ttu-id="9718a-138">Entrada (necessária)</span><span class="sxs-lookup"><span data-stu-id="9718a-138">Input (required)</span></span>|<span data-ttu-id="9718a-139">A cadeia de caracteres de entrada para procurar.</span><span class="sxs-lookup"><span data-stu-id="9718a-139">The input string to search.</span></span>|  
|<span data-ttu-id="9718a-140">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="9718a-140">RegexOptions</span></span>|<span data-ttu-id="9718a-141">Combinação OR bit a bit de [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="9718a-141">Bitwise OR combination of [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="9718a-142">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9718a-142">Return Value</span></span>|<span data-ttu-id="9718a-143"><xref:System.Text.RegularExpressions.MatchCollection> que contém a coleção de correspondências com êxito.</span><span class="sxs-lookup"><span data-stu-id="9718a-143">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="9718a-144">O exemplo de código demonstra como usar a atividade personalizado de `Matches` .</span><span class="sxs-lookup"><span data-stu-id="9718a-144">The following code example demonstrates how to use the `Matches` custom activity.</span></span>  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a><span data-ttu-id="9718a-145">Substituir</span><span class="sxs-lookup"><span data-stu-id="9718a-145">Replace</span></span>  
 <span data-ttu-id="9718a-146">A atividade personalizado de `Replace` procura uma cadeia de caracteres de entrada e substitui todas as cadeias de caracteres que correspondem a uma expressão regular especificada com uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9718a-146">The `Replace` custom activity searches an input string and replaces all strings that match a specified regular expression with a string.</span></span> <span data-ttu-id="9718a-147">A atividade deriva de <xref:System.Activities.CodeActivity%601> e dentro de <xref:System.Activities.CodeActivity%601.Execute%2A> o método chama o método de <xref:System.Text.RegularExpressions.Regex.Replace%2A> .</span><span class="sxs-lookup"><span data-stu-id="9718a-147">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method.</span></span>  
  
 <span data-ttu-id="9718a-148">A tabela a seguir descreve as propriedades e o valor de retorno para atividades personalizado de `Replace` .</span><span class="sxs-lookup"><span data-stu-id="9718a-148">The following table describes the properties and return value for the `Replace` custom activity.</span></span>  
  
|<span data-ttu-id="9718a-149">Propriedade ou valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9718a-149">Property or Return Value</span></span>|<span data-ttu-id="9718a-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="9718a-150">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="9718a-151">Padrão (necessário)</span><span class="sxs-lookup"><span data-stu-id="9718a-151">Pattern (required)</span></span>|<span data-ttu-id="9718a-152">A expressão regular com a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="9718a-152">The regular expression to search with.</span></span>|  
|<span data-ttu-id="9718a-153">Entrada (necessária)</span><span class="sxs-lookup"><span data-stu-id="9718a-153">Input (required)</span></span>|<span data-ttu-id="9718a-154">A cadeia de caracteres de entrada para procurar.</span><span class="sxs-lookup"><span data-stu-id="9718a-154">The input string to search.</span></span>|  
|<span data-ttu-id="9718a-155">Substituição</span><span class="sxs-lookup"><span data-stu-id="9718a-155">Replacement</span></span>|<span data-ttu-id="9718a-156">A cadeia de caracteres substituta.</span><span class="sxs-lookup"><span data-stu-id="9718a-156">The replacement string.</span></span><br /><br /> <span data-ttu-id="9718a-157">Se `Replacement` for especificado, então a propriedade de `MatchEvaluator` será ignorada.</span><span class="sxs-lookup"><span data-stu-id="9718a-157">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="9718a-158">`Replacement` ou propriedade de `MatchEvaluator` devem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="9718a-158">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="9718a-159">MatchEvaluator</span><span class="sxs-lookup"><span data-stu-id="9718a-159">MatchEvaluator</span></span>|<span data-ttu-id="9718a-160">Um método personalizado que examina cada correspondência e retorna a cadeia de caracteres correspondida original ou uma cadeia de caracteres de substituição.</span><span class="sxs-lookup"><span data-stu-id="9718a-160">A custom method that examines each match and returns either the original matched string or a replacement string.</span></span><br /><br /> <span data-ttu-id="9718a-161">Se `Replacement` for especificado, então a propriedade de `MatchEvaluator` será ignorada.</span><span class="sxs-lookup"><span data-stu-id="9718a-161">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="9718a-162">`Replacement` ou propriedade de `MatchEvaluator` devem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="9718a-162">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="9718a-163">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="9718a-163">RegexOptions</span></span>|<span data-ttu-id="9718a-164">Combinação OR bit a bit de [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="9718a-164">Bitwise OR combination of [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="9718a-165">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9718a-165">Return Value</span></span>|<span data-ttu-id="9718a-166"><xref:System.Text.RegularExpressions.MatchCollection> que contém a coleção de correspondências com êxito.</span><span class="sxs-lookup"><span data-stu-id="9718a-166">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="9718a-167">O exemplo de código demonstra como usar a atividade personalizado de `Replace` .</span><span class="sxs-lookup"><span data-stu-id="9718a-167">The following code example demonstrates how to use the `Replace` custom activity.</span></span>  
  
```  
// Using the replacement string.  
new Replace  
{  
    Pattern = @"\bWorld\b",  
    Input = "Hello World! This is a wonderful World",  
    Replacement = "Universe"  
};  
  
// Using a match evaluator.  
new Replace  
{  
    Pattern = new InArgument<string>(pattern),  
    Input = new InArgument<string>(input),  
    MatchEvaluator = new MatchEvaluator(CapText)                  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="9718a-168">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="9718a-168">To use this sample</span></span>  
  
1.  <span data-ttu-id="9718a-169">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de RegexActivities.sln.</span><span class="sxs-lookup"><span data-stu-id="9718a-169">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RegexActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="9718a-170">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="9718a-170">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="9718a-171">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="9718a-171">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9718a-172">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9718a-172">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9718a-173">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9718a-173">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9718a-174">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="9718a-174">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9718a-175">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9718a-175">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`