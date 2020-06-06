---
title: Esquema de configurações do aplicativo
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81242823"
---
# <a name="application-settings-schema"></a><span data-ttu-id="91f35-102">Esquema de configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="91f35-102">Application Settings schema</span></span>

<span data-ttu-id="91f35-103">As configurações de aplicativo permitem que um aplicativo Windows Forms ou ASP.NET armazene e recupere as configurações no escopo do aplicativo e em escopo do usuário.</span><span class="sxs-lookup"><span data-stu-id="91f35-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="91f35-104">Nesse contexto, uma *configuração* é qualquer informação que possa ser específica para o aplicativo ou específica para o usuário atual — tudo, desde uma cadeia de conexão de banco de dados até o tamanho de janela padrão preferencial do usuário.</span><span class="sxs-lookup"><span data-stu-id="91f35-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="91f35-105">Por padrão, as configurações do aplicativo em um aplicativo Windows Forms usam a <xref:System.Configuration.LocalFileSettingsProvider> classe, que usa o sistema de configuração do .net para armazenar as configurações em um arquivo de configuração XML.</span><span class="sxs-lookup"><span data-stu-id="91f35-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="91f35-106">Para obter mais informações sobre os arquivos usados pelas configurações do aplicativo, consulte [arquitetura de configurações do aplicativo](../../winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="91f35-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="91f35-107">Configurações de aplicativo define os seguintes elementos como parte dos arquivos de configuração que ele usa.</span><span class="sxs-lookup"><span data-stu-id="91f35-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="91f35-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="91f35-108">Element</span></span>                    | <span data-ttu-id="91f35-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="91f35-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | <span data-ttu-id="91f35-110">Contém todas as **\<setting>** marcas específicas para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91f35-110">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| **\<userSettings>**        | <span data-ttu-id="91f35-111">Contém todas as **\<setting>** marcas específicas do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="91f35-111">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| **\<setting>**             | <span data-ttu-id="91f35-112">Define uma configuração.</span><span class="sxs-lookup"><span data-stu-id="91f35-112">Defines a setting.</span></span> <span data-ttu-id="91f35-113">Filho de **\<applicationSettings>** ou **\<userSettings>** .</span><span class="sxs-lookup"><span data-stu-id="91f35-113">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| **\<value>**               | <span data-ttu-id="91f35-114">Define o valor de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="91f35-114">Defines a setting's value.</span></span> <span data-ttu-id="91f35-115">Filho de **\<setting>** .</span><span class="sxs-lookup"><span data-stu-id="91f35-115">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="91f35-116">Elemento \<applicationSettings></span><span class="sxs-lookup"><span data-stu-id="91f35-116">\<applicationSettings> element</span></span>

<span data-ttu-id="91f35-117">Esse elemento contém todas as **\<setting>** marcas que são específicas para uma instância do aplicativo em um computador cliente.</span><span class="sxs-lookup"><span data-stu-id="91f35-117">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="91f35-118">Não define nenhum atributo.</span><span class="sxs-lookup"><span data-stu-id="91f35-118">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="91f35-119">Elemento \<userSettings></span><span class="sxs-lookup"><span data-stu-id="91f35-119">\<userSettings> element</span></span>

<span data-ttu-id="91f35-120">Esse elemento contém todas as **\<setting>** marcas que são específicas para o usuário que está usando o aplicativo no momento.</span><span class="sxs-lookup"><span data-stu-id="91f35-120">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="91f35-121">Não define nenhum atributo.</span><span class="sxs-lookup"><span data-stu-id="91f35-121">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="91f35-122">Elemento \<setting></span><span class="sxs-lookup"><span data-stu-id="91f35-122">\<setting> element</span></span>

<span data-ttu-id="91f35-123">Esse elemento define uma configuração.</span><span class="sxs-lookup"><span data-stu-id="91f35-123">This element defines a setting.</span></span> <span data-ttu-id="91f35-124">Ele tem os atributos a seguir.</span><span class="sxs-lookup"><span data-stu-id="91f35-124">It has the following attributes.</span></span>

| <span data-ttu-id="91f35-125">Atributo</span><span class="sxs-lookup"><span data-stu-id="91f35-125">Attribute</span></span>        | <span data-ttu-id="91f35-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="91f35-126">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="91f35-127">**name**</span><span class="sxs-lookup"><span data-stu-id="91f35-127">**name**</span></span>         | <span data-ttu-id="91f35-128">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="91f35-128">Required.</span></span> <span data-ttu-id="91f35-129">A ID exclusiva da configuração.</span><span class="sxs-lookup"><span data-stu-id="91f35-129">The unique ID of the setting.</span></span> <span data-ttu-id="91f35-130">As configurações criadas por meio do Visual Studio são salvas com o nome `ProjectName.Properties.Settings` .</span><span class="sxs-lookup"><span data-stu-id="91f35-130">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="91f35-131">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="91f35-131">**serializeAs**</span></span> | <span data-ttu-id="91f35-132">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="91f35-132">Required.</span></span> <span data-ttu-id="91f35-133">O formato a ser usado para serializar o valor para texto.</span><span class="sxs-lookup"><span data-stu-id="91f35-133">The format to use for serializing the value to text.</span></span> <span data-ttu-id="91f35-134">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="91f35-134">Valid values are:</span></span><br><br><span data-ttu-id="91f35-135">- `string`.</span><span class="sxs-lookup"><span data-stu-id="91f35-135">- `string`.</span></span> <span data-ttu-id="91f35-136">O valor é serializado como uma cadeia de caracteres usando um <xref:System.ComponentModel.TypeConverter> .</span><span class="sxs-lookup"><span data-stu-id="91f35-136">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="91f35-137">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="91f35-137">- `xml`.</span></span> <span data-ttu-id="91f35-138">O valor é serializado usando a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="91f35-138">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="91f35-139">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="91f35-139">- `binary`.</span></span> <span data-ttu-id="91f35-140">O valor é serializado como binário codificado por texto usando serialização binária.</span><span class="sxs-lookup"><span data-stu-id="91f35-140">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="91f35-141">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="91f35-141">- `custom`.</span></span> <span data-ttu-id="91f35-142">O provedor de configurações tem um conhecimento inerente dessa configuração e a serializa e a desserializa.</span><span class="sxs-lookup"><span data-stu-id="91f35-142">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="91f35-143">Elemento \<value></span><span class="sxs-lookup"><span data-stu-id="91f35-143">\<value> element</span></span>

<span data-ttu-id="91f35-144">Esse elemento contém o valor de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="91f35-144">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="91f35-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="91f35-145">Example</span></span>

<span data-ttu-id="91f35-146">O exemplo a seguir mostra um arquivo de configurações do aplicativo que define duas configurações no escopo do aplicativo e duas configurações no escopo do usuário:</span><span class="sxs-lookup"><span data-stu-id="91f35-146">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="91f35-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="91f35-147">See also</span></span>

- [<span data-ttu-id="91f35-148">Visão geral das configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="91f35-148">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="91f35-149">Arquitetura das configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="91f35-149">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
