---
title: Esquema de configurações do aplicativo
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f11be59941759687806591feb1edcce28b2119e6
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844222"
---
# <a name="application-settings-schema"></a><span data-ttu-id="0b559-102">Esquema de configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="0b559-102">Application Settings schema</span></span>

<span data-ttu-id="0b559-103">As configurações de aplicativo permitem que um aplicativo Windows Forms ou do ASP.NET armazene e recupere configurações no escopo do aplicativo e no escopo do usuário.</span><span class="sxs-lookup"><span data-stu-id="0b559-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="0b559-104">Nesse contexto, uma *configuração* é qualquer informação que podem ser específicos do usuário atual ou específica do aplicativo — qualquer coisa, desde uma cadeia de caracteres de conexão de banco de dados para o usuário preferencial tamanho de janela padrão do.</span><span class="sxs-lookup"><span data-stu-id="0b559-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="0b559-105">Por padrão, as configurações do aplicativo em um aplicativo Windows Forms usa o <xref:System.Configuration.LocalFileSettingsProvider> classe, que usa o sistema de configuração do .NET para armazenar configurações em um arquivo de configuração XML.</span><span class="sxs-lookup"><span data-stu-id="0b559-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="0b559-106">Para obter mais informações sobre os arquivos usados pelas configurações de aplicativo, consulte [Application Settings Architecture](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="0b559-106">For more information about the files used by application settings, see [Application Settings Architecture](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="0b559-107">As configurações de aplicativo define os elementos a seguir como parte dos arquivos de configuração, ele usa.</span><span class="sxs-lookup"><span data-stu-id="0b559-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="0b559-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b559-108">Element</span></span>                    | <span data-ttu-id="0b559-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b559-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="0b559-110">**\<applicationSettings >**</span><span class="sxs-lookup"><span data-stu-id="0b559-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="0b559-111">Contém todos os  **\<Configuração >** marcas específicas para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0b559-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="0b559-112">**\<userSettings >**</span><span class="sxs-lookup"><span data-stu-id="0b559-112">**\<userSettings>**</span></span>        | <span data-ttu-id="0b559-113">Contém todos os  **\<Configuração >** marcas específicas para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="0b559-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="0b559-114">**\<Configuração >**</span><span class="sxs-lookup"><span data-stu-id="0b559-114">**\<setting>**</span></span>             | <span data-ttu-id="0b559-115">Define uma configuração.</span><span class="sxs-lookup"><span data-stu-id="0b559-115">Defines a setting.</span></span> <span data-ttu-id="0b559-116">Filho de um  **\<applicationSettings >** ou  **\<userSettings >**.</span><span class="sxs-lookup"><span data-stu-id="0b559-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="0b559-117">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="0b559-117">**\<value>**</span></span>               | <span data-ttu-id="0b559-118">Define um valor de configuração.</span><span class="sxs-lookup"><span data-stu-id="0b559-118">Defines a setting's value.</span></span> <span data-ttu-id="0b559-119">Filho de  **\<Configuração >**.</span><span class="sxs-lookup"><span data-stu-id="0b559-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="0b559-120">\<applicationSettings > elemento</span><span class="sxs-lookup"><span data-stu-id="0b559-120">\<applicationSettings> element</span></span>

<span data-ttu-id="0b559-121">Esse elemento contém todos os  **\<Configuração >** marcas que são específicas a uma instância do aplicativo em um computador cliente.</span><span class="sxs-lookup"><span data-stu-id="0b559-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="0b559-122">Não define nenhum atributo.</span><span class="sxs-lookup"><span data-stu-id="0b559-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="0b559-123">\<userSettings > elemento</span><span class="sxs-lookup"><span data-stu-id="0b559-123">\<userSettings> element</span></span>

<span data-ttu-id="0b559-124">Esse elemento contém todos os  **\<Configuração >** marcas que são específicas para o usuário que está usando atualmente o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0b559-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="0b559-125">Não define nenhum atributo.</span><span class="sxs-lookup"><span data-stu-id="0b559-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="0b559-126">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="0b559-126">\<setting> element</span></span>

<span data-ttu-id="0b559-127">Esse elemento define uma configuração.</span><span class="sxs-lookup"><span data-stu-id="0b559-127">This element defines a setting.</span></span> <span data-ttu-id="0b559-128">Ele tem os seguintes atributos.</span><span class="sxs-lookup"><span data-stu-id="0b559-128">It has the following attributes.</span></span>

| <span data-ttu-id="0b559-129">Atributo</span><span class="sxs-lookup"><span data-stu-id="0b559-129">Attribute</span></span>        | <span data-ttu-id="0b559-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b559-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="0b559-131">**name**</span><span class="sxs-lookup"><span data-stu-id="0b559-131">**name**</span></span>         | <span data-ttu-id="0b559-132">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0b559-132">Required.</span></span> <span data-ttu-id="0b559-133">A ID exclusiva da configuração.</span><span class="sxs-lookup"><span data-stu-id="0b559-133">The unique ID of the setting.</span></span> <span data-ttu-id="0b559-134">As configurações criadas por meio do Visual Studio são salvos com o nome `ProjectName.Properties.Settings`.</span><span class="sxs-lookup"><span data-stu-id="0b559-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="0b559-135">**serializedAs**</span><span class="sxs-lookup"><span data-stu-id="0b559-135">**serializedAs**</span></span> | <span data-ttu-id="0b559-136">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0b559-136">Required.</span></span> <span data-ttu-id="0b559-137">O formato a ser usado para serializar o valor em texto.</span><span class="sxs-lookup"><span data-stu-id="0b559-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="0b559-138">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="0b559-138">Valid values are:</span></span><br><br><span data-ttu-id="0b559-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="0b559-139">- `string`.</span></span> <span data-ttu-id="0b559-140">O valor é serializado como uma cadeia de caracteres usando um <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="0b559-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="0b559-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="0b559-141">- `xml`.</span></span> <span data-ttu-id="0b559-142">O valor é serializado usando a serialização de XML.</span><span class="sxs-lookup"><span data-stu-id="0b559-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="0b559-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="0b559-143">- `binary`.</span></span> <span data-ttu-id="0b559-144">O valor é serializado como texto codificado binário usando a serialização binária.</span><span class="sxs-lookup"><span data-stu-id="0b559-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="0b559-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="0b559-145">- `custom`.</span></span> <span data-ttu-id="0b559-146">O provedor de configurações possui conhecimento inerente dessa configuração e serializa e desserializa-o.</span><span class="sxs-lookup"><span data-stu-id="0b559-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="0b559-147">\<valor > elemento</span><span class="sxs-lookup"><span data-stu-id="0b559-147">\<value> element</span></span>

<span data-ttu-id="0b559-148">Esse elemento contém o valor de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="0b559-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="0b559-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0b559-149">Example</span></span>

<span data-ttu-id="0b559-150">O exemplo a seguir mostra um arquivo de configurações do aplicativo que define duas configurações no escopo do aplicativo e duas configurações de escopo do usuário:</span><span class="sxs-lookup"><span data-stu-id="0b559-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="0b559-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b559-151">See also</span></span>

<span data-ttu-id="0b559-152">[Visão geral sobre configurações de aplicativo](~/docs/framework/winforms/advanced/application-settings-overview.md) </span><span class="sxs-lookup"><span data-stu-id="0b559-152">[Application Settings Overview](~/docs/framework/winforms/advanced/application-settings-overview.md) </span></span>  
[<span data-ttu-id="0b559-153">Arquitetura das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="0b559-153">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
