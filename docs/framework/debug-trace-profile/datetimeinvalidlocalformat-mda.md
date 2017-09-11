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
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="9ed04-102">MDA dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="9ed04-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="9ed04-103">O MDA `dateTimeInvalidLocalFormat` é ativado quando uma instância <xref:System.DateTime> que é armazenada como um UTC (Horário Coordenado Universal) é formatada com um formato que se destina a ser usado apenas em instâncias <xref:System.DateTime> locais.</span><span class="sxs-lookup"><span data-stu-id="9ed04-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="9ed04-104">Esse MDA não é ativado em instâncias <xref:System.DateTime> não especificadas ou padrão.</span><span class="sxs-lookup"><span data-stu-id="9ed04-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="9ed04-105">Sintoma</span><span class="sxs-lookup"><span data-stu-id="9ed04-105">Symptom</span></span>  
 <span data-ttu-id="9ed04-106">Um aplicativo está serializando uma instância <xref:System.DateTime> UTC manualmente usando um formato de local:</span><span class="sxs-lookup"><span data-stu-id="9ed04-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="9ed04-107">Causa</span><span class="sxs-lookup"><span data-stu-id="9ed04-107">Cause</span></span>  
 <span data-ttu-id="9ed04-108">O formato “z” do método <xref:System.DateTime.ToString%2A?displayProperty=fullName> inclui o deslocamento de fuso horário local, por exemplo, “+10h” para a hora de Sydney.</span><span class="sxs-lookup"><span data-stu-id="9ed04-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=fullName> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="9ed04-109">Assim, ele só produzirá um resultado significativo se o valor da <xref:System.DateTime> for local.</span><span class="sxs-lookup"><span data-stu-id="9ed04-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="9ed04-110">Se o valor for a hora UTC, <xref:System.DateTime.ToString%2A?displayProperty=fullName> incluirá o deslocamento de fuso horário local, mas não exibirá nem ajustará o especificador de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="9ed04-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=fullName> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="9ed04-111">Resolução</span><span class="sxs-lookup"><span data-stu-id="9ed04-111">Resolution</span></span>  
 <span data-ttu-id="9ed04-112">As instâncias <xref:System.DateTime> UTC devem ser formatadas de modo que indiquem que são UTC.</span><span class="sxs-lookup"><span data-stu-id="9ed04-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="9ed04-113">O formato recomendado para horas UTC é usar um “z” para indicar a hora UTC:</span><span class="sxs-lookup"><span data-stu-id="9ed04-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="9ed04-114">Também há um formato “o” que serializa uma <xref:System.DateTime>, fazendo uso da propriedade <xref:System.DateTime.Kind%2A> que serializa corretamente, independentemente se a instância é local, UTC ou não especificada:</span><span class="sxs-lookup"><span data-stu-id="9ed04-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9ed04-115">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="9ed04-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="9ed04-116">Esse MDA não afeta o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9ed04-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9ed04-117">Saída</span><span class="sxs-lookup"><span data-stu-id="9ed04-117">Output</span></span>  
 <span data-ttu-id="9ed04-118">Não há nenhuma saída especial como resultado da ativação desse MDA. No entanto, a pilha de chamadas pode ser usada para determinar o local da chamada <xref:System.DateTime.ToString%2A> que ativou o MDA.</span><span class="sxs-lookup"><span data-stu-id="9ed04-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9ed04-119">Configuração</span><span class="sxs-lookup"><span data-stu-id="9ed04-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="9ed04-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ed04-120">Example</span></span>  
 <span data-ttu-id="9ed04-121">Considere um aplicativo que está serializando o valor <xref:System.DateTime> UTC indiretamente usando a classe <xref:System.Xml.XmlConvert> ou <xref:System.Data.DataSet>, conforme mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="9ed04-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="9ed04-122">As serializações <xref:System.Xml.XmlConvert> e <xref:System.Data.DataSet> usam formatos locais para a serialização, por padrão.</span><span class="sxs-lookup"><span data-stu-id="9ed04-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="9ed04-123">Opções adicionais são necessárias para serializar outros tipos de valores <xref:System.DateTime>, como UTC.</span><span class="sxs-lookup"><span data-stu-id="9ed04-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="9ed04-124">Para esse exemplo específico, passe `XmlDateTimeSerializationMode.RoundtripKind` para a chamada `ToString` em `XmlConvert`.</span><span class="sxs-lookup"><span data-stu-id="9ed04-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="9ed04-125">Isso serializa os dados como uma hora UTC.</span><span class="sxs-lookup"><span data-stu-id="9ed04-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="9ed04-126">Se estiver usando um <xref:System.Data.DataSet>, defina a propriedade <xref:System.Data.DataColumn.DateTimeMode%2A> no objeto <xref:System.Data.DataColumn> como <xref:System.Data.DataSetDateTime.Utc>.</span><span class="sxs-lookup"><span data-stu-id="9ed04-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ed04-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ed04-127">See Also</span></span>  
 <span data-ttu-id="9ed04-128"><xref:System.Globalization.DateTimeFormatInfo></span><span class="sxs-lookup"><span data-stu-id="9ed04-128"><xref:System.Globalization.DateTimeFormatInfo></span></span>   
 [<span data-ttu-id="9ed04-129">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="9ed04-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

