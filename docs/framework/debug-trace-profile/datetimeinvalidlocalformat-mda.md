---
title: MDA dateTimeInvalidLocalFormat
description: Examine o MDA (Assistente de depuração gerenciada) dateTimeInvalidLocalFormat, que é ativado quando um valor DateTime armazenado em UTC Obtém um formato DateTime somente local.
ms.date: 03/30/2017
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
ms.openlocfilehash: d092b93af55d2cdf14e9284d8cffcdc8440cbf81
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415986"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="2e536-103">MDA dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="2e536-103">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="2e536-104">O MDA `dateTimeInvalidLocalFormat` é ativado quando uma instância <xref:System.DateTime> que é armazenada como um UTC (Horário Coordenado Universal) é formatada com um formato que se destina a ser usado apenas em instâncias <xref:System.DateTime> locais.</span><span class="sxs-lookup"><span data-stu-id="2e536-104">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="2e536-105">Esse MDA não é ativado em instâncias <xref:System.DateTime> não especificadas ou padrão.</span><span class="sxs-lookup"><span data-stu-id="2e536-105">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="2e536-106">Sintoma</span><span class="sxs-lookup"><span data-stu-id="2e536-106">Symptom</span></span>  
 <span data-ttu-id="2e536-107">Um aplicativo está serializando uma instância <xref:System.DateTime> UTC manualmente usando um formato de local:</span><span class="sxs-lookup"><span data-stu-id="2e536-107">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="2e536-108">Causa</span><span class="sxs-lookup"><span data-stu-id="2e536-108">Cause</span></span>  
 <span data-ttu-id="2e536-109">O formato “z” do método <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> inclui o deslocamento de fuso horário local, por exemplo, “+10h” para a hora de Sydney.</span><span class="sxs-lookup"><span data-stu-id="2e536-109">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="2e536-110">Assim, ele só produzirá um resultado significativo se o valor da <xref:System.DateTime> for local.</span><span class="sxs-lookup"><span data-stu-id="2e536-110">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="2e536-111">Se o valor for a hora UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> incluirá o deslocamento de fuso horário local, mas não exibirá nem ajustará o especificador de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="2e536-111">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="2e536-112">Resolução</span><span class="sxs-lookup"><span data-stu-id="2e536-112">Resolution</span></span>  
 <span data-ttu-id="2e536-113">As instâncias <xref:System.DateTime> UTC devem ser formatadas de modo que indiquem que são UTC.</span><span class="sxs-lookup"><span data-stu-id="2e536-113">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="2e536-114">O formato recomendado para horas UTC é usar um “z” para indicar a hora UTC:</span><span class="sxs-lookup"><span data-stu-id="2e536-114">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="2e536-115">Também há um formato “o” que serializa uma <xref:System.DateTime>, fazendo uso da propriedade <xref:System.DateTime.Kind%2A> que serializa corretamente, independentemente se a instância é local, UTC ou não especificada:</span><span class="sxs-lookup"><span data-stu-id="2e536-115">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2e536-116">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="2e536-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="2e536-117">Esse MDA não afeta o runtime.</span><span class="sxs-lookup"><span data-stu-id="2e536-117">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2e536-118">Saída</span><span class="sxs-lookup"><span data-stu-id="2e536-118">Output</span></span>  
 <span data-ttu-id="2e536-119">Não há nenhuma saída especial como resultado da ativação desse MDA. No entanto, a pilha de chamadas pode ser usada para determinar o local da chamada <xref:System.DateTime.ToString%2A> que ativou o MDA.</span><span class="sxs-lookup"><span data-stu-id="2e536-119">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2e536-120">Configuração</span><span class="sxs-lookup"><span data-stu-id="2e536-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="2e536-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e536-121">Example</span></span>  
 <span data-ttu-id="2e536-122">Considere um aplicativo que está serializando o valor <xref:System.DateTime> UTC indiretamente usando a classe <xref:System.Xml.XmlConvert> ou <xref:System.Data.DataSet>, conforme mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="2e536-122">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="2e536-123">As serializações <xref:System.Xml.XmlConvert> e <xref:System.Data.DataSet> usam formatos locais para a serialização, por padrão.</span><span class="sxs-lookup"><span data-stu-id="2e536-123">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="2e536-124">Opções adicionais são necessárias para serializar outros tipos de valores <xref:System.DateTime>, como UTC.</span><span class="sxs-lookup"><span data-stu-id="2e536-124">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="2e536-125">Para esse exemplo específico, passe `XmlDateTimeSerializationMode.RoundtripKind` para a chamada `ToString` em `XmlConvert`.</span><span class="sxs-lookup"><span data-stu-id="2e536-125">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="2e536-126">Isso serializa os dados como uma hora UTC.</span><span class="sxs-lookup"><span data-stu-id="2e536-126">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="2e536-127">Se estiver usando um <xref:System.Data.DataSet>, defina a propriedade <xref:System.Data.DataColumn.DateTimeMode%2A> no objeto <xref:System.Data.DataColumn> como <xref:System.Data.DataSetDateTime.Utc>.</span><span class="sxs-lookup"><span data-stu-id="2e536-127">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e536-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="2e536-128">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="2e536-129">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="2e536-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
