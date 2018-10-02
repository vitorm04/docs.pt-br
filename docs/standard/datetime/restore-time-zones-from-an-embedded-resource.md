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
ms.openlocfilehash: 99d38b336b5e655dd1c96682eec90c5fbe8469d6
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030702"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="454e7-102">Como: restaurar fusos horários de um recurso inserido</span><span class="sxs-lookup"><span data-stu-id="454e7-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="454e7-103">Este tópico descreve como restaurar fusos horários que tenha sido salvo em um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="454e7-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="454e7-104">Para obter informações e instruções sobre como salvar fusos horários, consulte [como: salvar fusos horários em um recurso inserido](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span><span class="sxs-lookup"><span data-stu-id="454e7-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="454e7-105">Para desserializar um objeto TimeZoneInfo de um recurso inserido</span><span class="sxs-lookup"><span data-stu-id="454e7-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="454e7-106">Se o fuso horário a ser recuperado não for um fuso horário personalizado, tente criar uma instância dele usando o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> método.</span><span class="sxs-lookup"><span data-stu-id="454e7-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="454e7-107">Criar uma instância de um <xref:System.Resources.ResourceManager> objeto, passando o nome totalmente qualificado do arquivo de recurso inserido e uma referência ao assembly que contém o arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="454e7-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="454e7-108">Se você não puder determinar o nome totalmente qualificado do arquivo de recurso inserido, use o [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para examinar o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="454e7-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="454e7-109">Um `.mresource` entrada identifica o recurso.</span><span class="sxs-lookup"><span data-stu-id="454e7-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="454e7-110">No exemplo, o nome do recurso totalmente qualificado é `SerializeTimeZoneData.SerializedTimeZones`.</span><span class="sxs-lookup"><span data-stu-id="454e7-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="454e7-111">Se o arquivo de recurso é incorporado no mesmo assembly que contém o código de instanciação de fuso horário, você pode recuperar uma referência a ele, chamando o `static` (`Shared` no Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> método.</span><span class="sxs-lookup"><span data-stu-id="454e7-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="454e7-112">Se a chamada para o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> método falhar, ou se for um fuso horário personalizado a ser instanciado, recuperar uma cadeia de caracteres que contenha o fuso horário serializado chamando o <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="454e7-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="454e7-113">Desserialize os dados de fuso horário chamando o <xref:System.TimeZoneInfo.FromSerializedString%2A> método.</span><span class="sxs-lookup"><span data-stu-id="454e7-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="454e7-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="454e7-114">Example</span></span>

<span data-ttu-id="454e7-115">O exemplo a seguir desserializa um <xref:System.TimeZoneInfo> objeto armazenado em um arquivo de recurso XML .NET incorporado.</span><span class="sxs-lookup"><span data-stu-id="454e7-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="454e7-116">Esse código ilustra a manipulação de exceção para garantir que um <xref:System.TimeZoneInfo> objeto exigido pelo aplicativo está presente.</span><span class="sxs-lookup"><span data-stu-id="454e7-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="454e7-117">Ele primeiro tenta criar uma instância de um <xref:System.TimeZoneInfo> objeto por recuperá-los a partir do registro usando o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> método.</span><span class="sxs-lookup"><span data-stu-id="454e7-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="454e7-118">Se o fuso horário não pode ser instanciado, o código recupera do arquivo de recurso inserido.</span><span class="sxs-lookup"><span data-stu-id="454e7-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="454e7-119">Porque dados para fusos horários personalizados (fusos horários instanciados usando o <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método) não são armazenadas no registro, o código chama o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> para instanciar o fuso horário para Palmer, Antártica.</span><span class="sxs-lookup"><span data-stu-id="454e7-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="454e7-120">Em vez disso, ele imediatamente verifica o arquivo de recurso inserido para recuperar uma cadeia de caracteres que contém os dados da zona de tempo antes de chamar o <xref:System.TimeZoneInfo.FromSerializedString%2A> método.</span><span class="sxs-lookup"><span data-stu-id="454e7-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="454e7-121">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="454e7-121">Compiling the code</span></span>

<span data-ttu-id="454e7-122">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="454e7-122">This example requires:</span></span>

* <span data-ttu-id="454e7-123">Que uma referência à dll e dll seja adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="454e7-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="454e7-124">Se os seguintes namespaces sejam importados:</span><span class="sxs-lookup"><span data-stu-id="454e7-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="454e7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="454e7-125">See also</span></span>

* [<span data-ttu-id="454e7-126">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="454e7-126">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
* [<span data-ttu-id="454e7-127">Visão geral de fusos horários</span><span class="sxs-lookup"><span data-stu-id="454e7-127">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
* [<span data-ttu-id="454e7-128">Como salvar fusos horários em um recurso inserido</span><span class="sxs-lookup"><span data-stu-id="454e7-128">How to: Save time zones to an embedded resource</span></span>](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
