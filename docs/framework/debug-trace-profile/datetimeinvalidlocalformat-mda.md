---
title: MDA dateTimeInvalidLocalFormat
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- dates [.NET Framework], formatting
- invalid date time local format
- invalid local formats
- MDAs (managed debugging assistants), invalid local formats
- managed debugging assistants (MDAs), invalid local formats
- dateTimeInvalidLocalFormat MDA
- date formatting
- time formatting
- UTC formatting
ms.assetid: c4a942bb-2651-4b65-8718-809f892a0659
caps.latest.revision: 8
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 43155bb2eebfd2cd379d245715c100878fb9fb73
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="datetimeinvalidlocalformat-mda"></a>MDA dateTimeInvalidLocalFormat
O MDA `dateTimeInvalidLocalFormat` é ativado quando uma instância <xref:System.DateTime> que é armazenada como um UTC (Horário Coordenado Universal) é formatada com um formato que se destina a ser usado apenas em instâncias <xref:System.DateTime> locais. Esse MDA não é ativado em instâncias <xref:System.DateTime> não especificadas ou padrão.  
  
## <a name="symptom"></a>Sintoma  
 Um aplicativo está serializando uma instância <xref:System.DateTime> UTC manualmente usando um formato de local:  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Causa  
 O formato “z” do método <xref:System.DateTime.ToString%2A?displayProperty=fullName> inclui o deslocamento de fuso horário local, por exemplo, “+10h” para a hora de Sydney. Assim, ele só produzirá um resultado significativo se o valor da <xref:System.DateTime> for local. Se o valor for a hora UTC, <xref:System.DateTime.ToString%2A?displayProperty=fullName> incluirá o deslocamento de fuso horário local, mas não exibirá nem ajustará o especificador de fuso horário.  
  
### <a name="resolution"></a>Resolução  
 As instâncias <xref:System.DateTime> UTC devem ser formatadas de modo que indiquem que são UTC. O formato recomendado para horas UTC é usar um “z” para indicar a hora UTC:  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Também há um formato “o” que serializa uma <xref:System.DateTime>, fazendo uso da propriedade <xref:System.DateTime.Kind%2A> que serializa corretamente, independentemente se a instância é local, UTC ou não especificada:  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Esse MDA não afeta o tempo de execução.  
  
## <a name="output"></a>Saída  
 Não há nenhuma saída especial como resultado da ativação desse MDA. No entanto, a pilha de chamadas pode ser usada para determinar o local da chamada <xref:System.DateTime.ToString%2A> que ativou o MDA.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Exemplo  
 Considere um aplicativo que está serializando o valor <xref:System.DateTime> UTC indiretamente usando a classe <xref:System.Xml.XmlConvert> ou <xref:System.Data.DataSet>, conforme mostrado a seguir.  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 As serializações <xref:System.Xml.XmlConvert> e <xref:System.Data.DataSet> usam formatos locais para a serialização, por padrão. Opções adicionais são necessárias para serializar outros tipos de valores <xref:System.DateTime>, como UTC.  
  
 Para esse exemplo específico, passe `XmlDateTimeSerializationMode.RoundtripKind` para a chamada `ToString` em `XmlConvert`. Isso serializa os dados como uma hora UTC.  
  
 Se estiver usando um <xref:System.Data.DataSet>, defina a propriedade <xref:System.Data.DataColumn.DateTimeMode%2A> no objeto <xref:System.Data.DataColumn> como <xref:System.Data.DataSetDateTime.Utc>.  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Globalization.DateTimeFormatInfo>   
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

