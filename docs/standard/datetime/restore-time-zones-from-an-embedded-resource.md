---
title: 'Como: restaurar fusos horários de um recurso inserido'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98813bf6685be78d33ebd5cc5e8c07a61a811c25
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106757"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="004c8-102">Como: restaurar fusos horários de um recurso inserido</span><span class="sxs-lookup"><span data-stu-id="004c8-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="004c8-103">Este tópico descreve como restaurar os fusos horários que foram salvos em um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="004c8-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="004c8-104">Para obter informações e instruções sobre como salvar fusos [horários, consulte Como: Salve fusos horários em um recurso](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)inserido.</span><span class="sxs-lookup"><span data-stu-id="004c8-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="004c8-105">Para desserializar um objeto TimeZoneInfo de um recurso inserido</span><span class="sxs-lookup"><span data-stu-id="004c8-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="004c8-106">Se o fuso horário a ser recuperado não for um fuso horário personalizado, tente instanciá-lo usando o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> método.</span><span class="sxs-lookup"><span data-stu-id="004c8-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="004c8-107">Crie uma <xref:System.Resources.ResourceManager> instância de um objeto passando o nome totalmente qualificado do arquivo de recurso inserido e uma referência para o assembly que contém o arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="004c8-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="004c8-108">Se você não puder determinar o nome totalmente qualificado do arquivo de recurso inserido, use o [ILDASM. exe (desmontador de Il)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para examinar o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="004c8-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="004c8-109">Uma `.mresource` entrada identifica o recurso.</span><span class="sxs-lookup"><span data-stu-id="004c8-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="004c8-110">No exemplo, o nome totalmente qualificado do recurso é `SerializeTimeZoneData.SerializedTimeZones`.</span><span class="sxs-lookup"><span data-stu-id="004c8-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="004c8-111">Se o arquivo de recurso for inserido no mesmo assembly que contém o código de instanciação de fuso horário, você poderá recuperar uma referência a ele chamando `static` o`Shared` método (no <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="004c8-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="004c8-112">Se a chamada para o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> método falhar ou se um fuso horário personalizado for ser instanciado, recupere uma cadeia de caracteres que contenha o fuso horário serializado chamando o <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="004c8-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="004c8-113">Desserializar os dados de fuso horário chamando o <xref:System.TimeZoneInfo.FromSerializedString%2A> método.</span><span class="sxs-lookup"><span data-stu-id="004c8-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="004c8-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="004c8-114">Example</span></span>

<span data-ttu-id="004c8-115">O exemplo a seguir desserializa um <xref:System.TimeZoneInfo> objeto armazenado em um arquivo de recurso XML do .net inserido.</span><span class="sxs-lookup"><span data-stu-id="004c8-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="004c8-116">Esse código ilustra a manipulação de exceção para garantir <xref:System.TimeZoneInfo> que um objeto exigido pelo aplicativo esteja presente.</span><span class="sxs-lookup"><span data-stu-id="004c8-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="004c8-117">Primeiro, ele tenta criar uma <xref:System.TimeZoneInfo> instância de um objeto recuperando-o do registro <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> usando o método.</span><span class="sxs-lookup"><span data-stu-id="004c8-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="004c8-118">Se o fuso horário não puder ser instanciado, o código o recuperará do arquivo de recurso inserido.</span><span class="sxs-lookup"><span data-stu-id="004c8-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="004c8-119">Como os dados de fusos horários personalizados (fusos horários instanciados <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> usando o método) não são armazenados no registro, o código não chama o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> para instanciar o fuso horário para Palmer, Antártica.</span><span class="sxs-lookup"><span data-stu-id="004c8-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="004c8-120">Em vez disso, ele procura imediatamente o arquivo de recurso inserido para recuperar uma cadeia de caracteres que contém os dados do fuso horário <xref:System.TimeZoneInfo.FromSerializedString%2A> antes de chamar o método.</span><span class="sxs-lookup"><span data-stu-id="004c8-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="004c8-121">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="004c8-121">Compiling the code</span></span>

<span data-ttu-id="004c8-122">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="004c8-122">This example requires:</span></span>

- <span data-ttu-id="004c8-123">Que uma referência a System. Windows. Forms. dll e System. Core. dll seja adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="004c8-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="004c8-124">Que os seguintes namespaces sejam importados:</span><span class="sxs-lookup"><span data-stu-id="004c8-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="004c8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="004c8-125">See also</span></span>

- [<span data-ttu-id="004c8-126">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="004c8-126">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="004c8-127">Visão geral de fusos horários</span><span class="sxs-lookup"><span data-stu-id="004c8-127">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="004c8-128">Como: Salvar fusos horários em um recurso inserido</span><span class="sxs-lookup"><span data-stu-id="004c8-128">How to: Save time zones to an embedded resource</span></span>](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
