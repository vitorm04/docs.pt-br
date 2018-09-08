---
title: Atividades de expressão regular
ms.date: 03/30/2017
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
ms.openlocfilehash: 50daa5b6d7baab37f372de4c30c2e0d12b4fa943
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201004"
---
# <a name="regular-expression-activities"></a>Atividades de expressão regular
Este exemplo demonstra como criar um conjunto de atividades que expõe a funcionalidade de expressões regulares do <xref:System.Text.RegularExpressions> . Essas atividades personalizados podem ser usadas em um aplicativo de fluxo de trabalho. Para obter mais informações sobre expressões regulares, consulte [RegularExpressions](https://go.microsoft.com/fwlink/?LinkId=150434) Namespace.  
  
 A tabela a seguir detalha as atividades personalizados nesse exemplo.  
  
|Atividade|Descrição|  
|--------------|-----------------|  
|IsMatch|Especifica se a expressão regular encontrado uma correspondência na cadeia de caracteres de entrada.|  
|Correspondências|Procura uma cadeia de caracteres de entrada por todas as ocorrências de uma expressão regular e retorna todas as correspondências com êxito.|  
|Substituir|Dentro de uma cadeia de caracteres especificada de entrada, substitui as cadeias de caracteres que correspondem um padrão de expressão regular com uma cadeia de caracteres especificada de substituição.|  
  
## <a name="ismatch"></a>IsMatch  
 A atividade personalizado de `IsMatch` retorna `true` se a propriedade de cadeia de caracteres de `Input` encontra uma correspondência na expressão regular especificada na propriedade de `Pattern` . A atividade deriva de <xref:System.Activities.CodeActivity%601> e dentro de <xref:System.Activities.CodeActivity%601.Execute%2A> o método chama o método de <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> .  
  
 A tabela a seguir descreve as propriedades e o valor de retorno para atividades personalizado de `IsMatch` .  
  
|Propriedade ou valor de retorno|Descrição|  
|------------------------------|-----------------|  
|Padrão (necessário)|A expressão regular com a pesquisa.|  
|Entrada (necessária)|A cadeia de caracteres de entrada para procurar.|  
|RegexOptions|Combinação OR bit a bit de [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) valores de enumeração.|  
|Valor retornado|`true` se a entrada encontra uma correspondência no padrão fornecido; se não `false`.|  
  
 O exemplo de código demonstra como usar a atividade personalizado de `IsMatch` .  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a>Correspondências  
 A atividade personalizado de `Matches` procura uma cadeia de caracteres de entrada por todas as ocorrências de uma expressão regular e retorna todas as correspondências com êxito. A atividade deriva de <xref:System.Activities.CodeActivity%601> e dentro de <xref:System.Activities.CodeActivity%601.Execute%2A> o método chama o método de <xref:System.Text.RegularExpressions.Regex.Matches%2A> .  
  
 A tabela a seguir descreve as propriedades e o valor de retorno para atividades personalizado de `IsMatch` .  
  
|Propriedade ou valor de retorno|Descrição|  
|------------------------------|-----------------|  
|Padrão (necessário)|A expressão regular com a pesquisa.|  
|Entrada (necessária)|A cadeia de caracteres de entrada para procurar.|  
|RegexOptions|Combinação OR bit a bit de [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) valores de enumeração.|  
|Valor de retorno|<xref:System.Text.RegularExpressions.MatchCollection> que contém a coleção de correspondências com êxito.|  
  
 O exemplo de código demonstra como usar a atividade personalizado de `Matches` .  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a>Substituir  
 A atividade personalizado de `Replace` procura uma cadeia de caracteres de entrada e substitui todas as cadeias de caracteres que correspondem a uma expressão regular especificada com uma cadeia de caracteres. A atividade deriva de <xref:System.Activities.CodeActivity%601> e dentro de <xref:System.Activities.CodeActivity%601.Execute%2A> o método chama o método de <xref:System.Text.RegularExpressions.Regex.Replace%2A> .  
  
 A tabela a seguir descreve as propriedades e o valor de retorno para atividades personalizado de `Replace` .  
  
|Propriedade ou valor de retorno|Descrição|  
|------------------------------|-----------------|  
|Padrão (necessário)|A expressão regular com a pesquisa.|  
|Entrada (necessária)|A cadeia de caracteres de entrada para procurar.|  
|Substituição|A cadeia de caracteres substituta.<br /><br /> Se `Replacement` for especificado, então a propriedade de `MatchEvaluator` será ignorada. `Replacement` ou propriedade de `MatchEvaluator` devem ser definidos.|  
|MatchEvaluator|Um método personalizado que examina cada correspondência e retorna a cadeia de caracteres correspondida original ou uma cadeia de caracteres de substituição.<br /><br /> Se `Replacement` for especificado, então a propriedade de `MatchEvaluator` será ignorada. `Replacement` ou propriedade de `MatchEvaluator` devem ser definidos.|  
|RegexOptions|Combinação OR bit a bit de [RegexOptions](https://go.microsoft.com/fwlink/?LinkId=150446) valores de enumeração.|  
|Valor de retorno|<xref:System.Text.RegularExpressions.MatchCollection> que contém a coleção de correspondências com êxito.|  
  
 O exemplo de código demonstra como usar a atividade personalizado de `Replace` .  
  
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
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de RegexActivities.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`