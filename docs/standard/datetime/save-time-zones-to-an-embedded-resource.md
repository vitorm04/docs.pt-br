---
title: 'Como: salvar fusos horários em um recurso inserido'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 921874e774d18751c29db495dac1bc53d10cc8ad
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44337714"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="91b8a-102">Como: salvar fusos horários em um recurso inserido</span><span class="sxs-lookup"><span data-stu-id="91b8a-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="91b8a-103">Um aplicativo com reconhecimento de fuso horário geralmente exige a presença de um determinado fuso horário.</span><span class="sxs-lookup"><span data-stu-id="91b8a-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="91b8a-104">No entanto, como a disponibilidade do indivíduo <xref:System.TimeZoneInfo> objetos depende de informações armazenadas no registro do sistema local, fusos horários disponíveis até mesmo normalmente pode estar ausentes.</span><span class="sxs-lookup"><span data-stu-id="91b8a-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="91b8a-105">Além disso, informações sobre fusos horários personalizados é instanciado usando o <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método não são armazenadas com outras informações de fuso horário no registro.</span><span class="sxs-lookup"><span data-stu-id="91b8a-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="91b8a-106">Para garantir que essas zonas de tempo estejam disponíveis quando eles forem necessários, salvá-los ao serializá-los e depois restaurá-los por desserializá-las.</span><span class="sxs-lookup"><span data-stu-id="91b8a-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="91b8a-107">Normalmente, serializar uma <xref:System.TimeZoneInfo> objeto ocorre além do aplicativo com reconhecimento de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="91b8a-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="91b8a-108">Dependendo do armazenamento de dados usado para manter serializado <xref:System.TimeZoneInfo> objetos, dados de fuso horário podem ser serializados como parte de uma rotina de instalação (por exemplo, quando os dados são armazenados em uma chave do registro de aplicativo), ou como parte de uma rotina de utilitário que é executado antes do aplicativo final é compilado (por exemplo, quando os dados serializados são armazenados em um arquivo de recurso (. resx) de XML do .NET).</span><span class="sxs-lookup"><span data-stu-id="91b8a-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="91b8a-109">Além de um arquivo de recurso que é compilado com o aplicativo, vários outros armazenamentos de dados podem ser usados para obter informações de fuso horário.</span><span class="sxs-lookup"><span data-stu-id="91b8a-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="91b8a-110">Eles incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="91b8a-110">These include the following:</span></span>

* <span data-ttu-id="91b8a-111">O registro.</span><span class="sxs-lookup"><span data-stu-id="91b8a-111">The registry.</span></span> <span data-ttu-id="91b8a-112">Observe que um aplicativo deve usar as subchaves da sua própria chave de aplicativo para armazenar dados de fuso horário personalizado em vez de utilizar as subchaves de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span><span class="sxs-lookup"><span data-stu-id="91b8a-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

* <span data-ttu-id="91b8a-113">Arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="91b8a-113">Configuration files.</span></span>

* <span data-ttu-id="91b8a-114">Outros arquivos do sistema.</span><span class="sxs-lookup"><span data-stu-id="91b8a-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="91b8a-115">Para salvar uma zona de tempo serializando-a para um arquivo. resx</span><span class="sxs-lookup"><span data-stu-id="91b8a-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="91b8a-116">Recuperar uma zona de tempo existente ou crie um novo fuso horário.</span><span class="sxs-lookup"><span data-stu-id="91b8a-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="91b8a-117">Para recuperar uma zona de tempo existente, consulte [como: acessar os objetos de fuso horário UTC e local predefinidos](../../../docs/standard/datetime/access-utc-and-local.md) e [como: instanciar um objeto TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="91b8a-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="91b8a-118">Para criar um novo fuso horário, chame uma das sobrecargas do <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método.</span><span class="sxs-lookup"><span data-stu-id="91b8a-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="91b8a-119">Para obter mais informações, consulte [como: criar fusos horários sem regras de ajuste](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) e [como: criar fusos horários com regras de ajuste](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="91b8a-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="91b8a-120">Chamar o <xref:System.TimeZoneInfo.ToSerializedString%2A> método para criar uma cadeia de caracteres que contém os dados do fuso horário.</span><span class="sxs-lookup"><span data-stu-id="91b8a-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="91b8a-121">Criar uma instância de um <xref:System.IO.StreamWriter> objeto, fornecendo o nome e, opcionalmente, o caminho do arquivo. resx para o <xref:System.IO.StreamWriter> construtor de classe.</span><span class="sxs-lookup"><span data-stu-id="91b8a-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="91b8a-122">Criar uma instância de um <xref:System.Resources.ResXResourceWriter> objeto, passando a <xref:System.IO.StreamWriter> do objeto para o <xref:System.Resources.ResXResourceWriter> construtor de classe.</span><span class="sxs-lookup"><span data-stu-id="91b8a-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="91b8a-123">Passe o fuso horário serializada de cadeia de caracteres para o <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="91b8a-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="91b8a-124">Chame o método <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="91b8a-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="91b8a-125">Chame o método <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="91b8a-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="91b8a-126">Fechar o <xref:System.IO.StreamWriter> objeto chamando seu <xref:System.IO.StreamWriter.Close%2A> método.</span><span class="sxs-lookup"><span data-stu-id="91b8a-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="91b8a-127">Adicione o arquivo. resx gerado ao projeto do Visual Studio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91b8a-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="91b8a-128">Usando o **propriedades** janela no Visual Studio, certifique-se de que o arquivo. resx **Build Action** estiver definida como **Embedded Resource**.</span><span class="sxs-lookup"><span data-stu-id="91b8a-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="91b8a-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="91b8a-129">Example</span></span>

<span data-ttu-id="91b8a-130">O exemplo a seguir serializa um <xref:System.TimeZoneInfo> objeto que representa o horário padrão Central e um <xref:System.TimeZoneInfo> objeto que representa a Estação Palmer, a hora da Antártida para um arquivo de recurso XML .NET chamado SerializedTimeZones.</span><span class="sxs-lookup"><span data-stu-id="91b8a-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="91b8a-131">Horário padrão Central normalmente é definido no registro. Estação Palmer, Antártica é um fuso horário personalizado.</span><span class="sxs-lookup"><span data-stu-id="91b8a-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="91b8a-132">Este exemplo serializa <xref:System.TimeZoneInfo> objetos para que eles estejam disponíveis em um arquivo de recurso em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="91b8a-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="91b8a-133">Porque o <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> método adiciona informações de cabeçalho completo para um arquivo de recurso XML .NET, ele não pode ser usado para adicionar recursos a um arquivo existente.</span><span class="sxs-lookup"><span data-stu-id="91b8a-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="91b8a-134">O exemplo lida com isso verificando o arquivo SerializedTimeZones e, se ele existir, armazenando todos os seus recursos diferentes dois serializado fusos horários um genérico <xref:System.Collections.Generic.Dictionary%602> objeto.</span><span class="sxs-lookup"><span data-stu-id="91b8a-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="91b8a-135">O arquivo existente é excluído e os recursos existentes são adicionados a um novo arquivo SerializedTimeZones.</span><span class="sxs-lookup"><span data-stu-id="91b8a-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="91b8a-136">Os dados da zona de tempo serializado também são adicionados a esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="91b8a-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="91b8a-137">A chave (ou **nome**) campos de recursos não devem conter espaços inseridos.</span><span class="sxs-lookup"><span data-stu-id="91b8a-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="91b8a-138">O <xref:System.String.Replace%28System.String%2CSystem.String%29> método é chamado para remover todos os espaços inseridos em identificadores de fuso horário, antes que eles sejam atribuídos ao arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="91b8a-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="91b8a-139">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="91b8a-139">Compiling the code</span></span>

<span data-ttu-id="91b8a-140">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="91b8a-140">This example requires:</span></span>

* <span data-ttu-id="91b8a-141">Que uma referência à dll e dll seja adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="91b8a-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="91b8a-142">Se os seguintes namespaces sejam importados:</span><span class="sxs-lookup"><span data-stu-id="91b8a-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="91b8a-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91b8a-143">See also</span></span>

* [<span data-ttu-id="91b8a-144">Datas, horas e fusos horários</span><span class="sxs-lookup"><span data-stu-id="91b8a-144">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
* [<span data-ttu-id="91b8a-145">Visão geral de fusos horários</span><span class="sxs-lookup"><span data-stu-id="91b8a-145">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
* [<span data-ttu-id="91b8a-146">Como restaurar fusos horários de um recurso inserido</span><span class="sxs-lookup"><span data-stu-id="91b8a-146">How to: Restore time zones from an embedded resource</span></span>](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
