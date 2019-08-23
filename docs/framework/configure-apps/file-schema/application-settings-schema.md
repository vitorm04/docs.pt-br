---
title: Esquema de configurações do aplicativo
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 89a08434332b0242fe57e9dcaa3b3ebcc5692d06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927758"
---
# <a name="application-settings-schema"></a><span data-ttu-id="b410a-102">Esquema de configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="b410a-102">Application Settings schema</span></span>

<span data-ttu-id="b410a-103">As configurações de aplicativo permitem que um aplicativo Windows Forms ou ASP.NET armazene e recupere as configurações no escopo do aplicativo e em escopo do usuário.</span><span class="sxs-lookup"><span data-stu-id="b410a-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="b410a-104">Nesse contexto, uma *configuração* é qualquer informação que possa ser específica para o aplicativo ou específica para o usuário atual — tudo, desde uma cadeia de conexão de banco de dados até o tamanho de janela padrão preferencial do usuário.</span><span class="sxs-lookup"><span data-stu-id="b410a-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="b410a-105">Por padrão, as configurações do aplicativo em um aplicativo Windows Forms <xref:System.Configuration.LocalFileSettingsProvider> usam a classe, que usa o sistema de configuração do .net para armazenar as configurações em um arquivo de configuração XML.</span><span class="sxs-lookup"><span data-stu-id="b410a-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="b410a-106">Para obter mais informações sobre os arquivos usados pelas configurações do aplicativo, consulte [arquitetura de configurações do aplicativo](../../winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="b410a-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="b410a-107">Configurações de aplicativo define os seguintes elementos como parte dos arquivos de configuração que ele usa.</span><span class="sxs-lookup"><span data-stu-id="b410a-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="b410a-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="b410a-108">Element</span></span>                    | <span data-ttu-id="b410a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b410a-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="b410a-110">**\<applicationSettings>**</span><span class="sxs-lookup"><span data-stu-id="b410a-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="b410a-111">Contém todas  **\<** as marcas de > de configuração específicas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b410a-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="b410a-112">**\<userSettings>**</span><span class="sxs-lookup"><span data-stu-id="b410a-112">**\<userSettings>**</span></span>        | <span data-ttu-id="b410a-113">Contém todas  **\<** as marcas de > de configuração específicas do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="b410a-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="b410a-114">**\<> de configuração**</span><span class="sxs-lookup"><span data-stu-id="b410a-114">**\<setting>**</span></span>             | <span data-ttu-id="b410a-115">Define uma configuração.</span><span class="sxs-lookup"><span data-stu-id="b410a-115">Defines a setting.</span></span> <span data-ttu-id="b410a-116">**O\<filho de ApplicationSettings >** ou  **\<UserSettings >** .</span><span class="sxs-lookup"><span data-stu-id="b410a-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="b410a-117">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="b410a-117">**\<value>**</span></span>               | <span data-ttu-id="b410a-118">Define o valor de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="b410a-118">Defines a setting's value.</span></span> <span data-ttu-id="b410a-119">Filho da  **\<configuração >** .</span><span class="sxs-lookup"><span data-stu-id="b410a-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="b410a-120">\<elemento applicationSettings ></span><span class="sxs-lookup"><span data-stu-id="b410a-120">\<applicationSettings> element</span></span>

<span data-ttu-id="b410a-121">Esse elemento contém todas  **\<** as marcas de > de configuração que são específicas para uma instância do aplicativo em um computador cliente.</span><span class="sxs-lookup"><span data-stu-id="b410a-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="b410a-122">Não define nenhum atributo.</span><span class="sxs-lookup"><span data-stu-id="b410a-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="b410a-123">\<UserSettings > elemento</span><span class="sxs-lookup"><span data-stu-id="b410a-123">\<userSettings> element</span></span>

<span data-ttu-id="b410a-124">Esse elemento contém todas  **\<** as marcas de > de configuração que são específicas para o usuário que está usando o aplicativo no momento.</span><span class="sxs-lookup"><span data-stu-id="b410a-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="b410a-125">Não define nenhum atributo.</span><span class="sxs-lookup"><span data-stu-id="b410a-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="b410a-126">\<definindo > elemento</span><span class="sxs-lookup"><span data-stu-id="b410a-126">\<setting> element</span></span>

<span data-ttu-id="b410a-127">Esse elemento define uma configuração.</span><span class="sxs-lookup"><span data-stu-id="b410a-127">This element defines a setting.</span></span> <span data-ttu-id="b410a-128">Ele tem os atributos a seguir.</span><span class="sxs-lookup"><span data-stu-id="b410a-128">It has the following attributes.</span></span>

| <span data-ttu-id="b410a-129">Atributo</span><span class="sxs-lookup"><span data-stu-id="b410a-129">Attribute</span></span>        | <span data-ttu-id="b410a-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="b410a-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="b410a-131">**name**</span><span class="sxs-lookup"><span data-stu-id="b410a-131">**name**</span></span>         | <span data-ttu-id="b410a-132">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b410a-132">Required.</span></span> <span data-ttu-id="b410a-133">A ID exclusiva da configuração.</span><span class="sxs-lookup"><span data-stu-id="b410a-133">The unique ID of the setting.</span></span> <span data-ttu-id="b410a-134">As configurações criadas por meio do Visual Studio são salvas com o nome `ProjectName.Properties.Settings`.</span><span class="sxs-lookup"><span data-stu-id="b410a-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="b410a-135">**serializedAs**</span><span class="sxs-lookup"><span data-stu-id="b410a-135">**serializedAs**</span></span> | <span data-ttu-id="b410a-136">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b410a-136">Required.</span></span> <span data-ttu-id="b410a-137">O formato a ser usado para serializar o valor para texto.</span><span class="sxs-lookup"><span data-stu-id="b410a-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="b410a-138">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="b410a-138">Valid values are:</span></span><br><br><span data-ttu-id="b410a-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="b410a-139">- `string`.</span></span> <span data-ttu-id="b410a-140">O valor é serializado como uma cadeia de caracteres <xref:System.ComponentModel.TypeConverter>usando um.</span><span class="sxs-lookup"><span data-stu-id="b410a-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="b410a-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="b410a-141">- `xml`.</span></span> <span data-ttu-id="b410a-142">O valor é serializado usando a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="b410a-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="b410a-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="b410a-143">- `binary`.</span></span> <span data-ttu-id="b410a-144">O valor é serializado como binário codificado por texto usando serialização binária.</span><span class="sxs-lookup"><span data-stu-id="b410a-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="b410a-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="b410a-145">- `custom`.</span></span> <span data-ttu-id="b410a-146">O provedor de configurações tem um conhecimento inerente dessa configuração e a serializa e a desserializa.</span><span class="sxs-lookup"><span data-stu-id="b410a-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="b410a-147">\<elemento de > de valor</span><span class="sxs-lookup"><span data-stu-id="b410a-147">\<value> element</span></span>

<span data-ttu-id="b410a-148">Esse elemento contém o valor de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="b410a-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="b410a-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b410a-149">Example</span></span>

<span data-ttu-id="b410a-150">O exemplo a seguir mostra um arquivo de configurações do aplicativo que define duas configurações no escopo do aplicativo e duas configurações no escopo do usuário:</span><span class="sxs-lookup"><span data-stu-id="b410a-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b410a-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b410a-151">See also</span></span>

- [<span data-ttu-id="b410a-152">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="b410a-152">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="b410a-153">Arquitetura das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="b410a-153">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
