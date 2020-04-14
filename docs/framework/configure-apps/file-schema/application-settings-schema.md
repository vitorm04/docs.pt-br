---
title: Esquema de configurações de aplicativos
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242823"
---
# <a name="application-settings-schema"></a><span data-ttu-id="20d8e-102">Esquema de configurações de aplicativos</span><span class="sxs-lookup"><span data-stu-id="20d8e-102">Application Settings schema</span></span>

<span data-ttu-id="20d8e-103">As configurações do aplicativo permitem que um aplicativo do Windows Forms ou ASP.NET armazene e recupere configurações com escopo de aplicativo e escopo do usuário.</span><span class="sxs-lookup"><span data-stu-id="20d8e-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="20d8e-104">Neste contexto, uma *configuração* é qualquer informação que possa ser específica para o aplicativo ou específica para o usuário atual — qualquer coisa, desde uma seqüência de conexão de banco de dados até o tamanho padrão de janela preferido do usuário.</span><span class="sxs-lookup"><span data-stu-id="20d8e-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="20d8e-105">Por padrão, as configurações do aplicativo <xref:System.Configuration.LocalFileSettingsProvider> em um aplicativo Do Windows Forms usam a classe, que usa o sistema de configuração .NET para armazenar configurações em um arquivo de configuração XML.</span><span class="sxs-lookup"><span data-stu-id="20d8e-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="20d8e-106">Para obter mais informações sobre os arquivos usados pelas configurações do aplicativo, consulte [Arquitetura de configurações de aplicativo](../../winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="20d8e-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="20d8e-107">As configurações do aplicativo definem os seguintes elementos como parte dos arquivos de configuração que ele usa.</span><span class="sxs-lookup"><span data-stu-id="20d8e-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="20d8e-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="20d8e-108">Element</span></span>                    | <span data-ttu-id="20d8e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="20d8e-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="20d8e-110">**\<configurações de aplicativos>**</span><span class="sxs-lookup"><span data-stu-id="20d8e-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="20d8e-111">Contém todas as \*\* \<configurações>\*\* tags específicas para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="20d8e-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="20d8e-112">**\<>de configurações de usuário**</span><span class="sxs-lookup"><span data-stu-id="20d8e-112">**\<userSettings>**</span></span>        | <span data-ttu-id="20d8e-113">Contém todas as \*\* \<configurações>\*\* tags específicas para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="20d8e-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="20d8e-114">**\<configuração>**</span><span class="sxs-lookup"><span data-stu-id="20d8e-114">**\<setting>**</span></span>             | <span data-ttu-id="20d8e-115">Define uma configuração.</span><span class="sxs-lookup"><span data-stu-id="20d8e-115">Defines a setting.</span></span> <span data-ttu-id="20d8e-116">Filho de \*\* \<configurações de aplicativosConfigurações>\*\* ou \*\* \<>de configurações do usuário \*\*.</span><span class="sxs-lookup"><span data-stu-id="20d8e-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="20d8e-117">**\<>de valores**</span><span class="sxs-lookup"><span data-stu-id="20d8e-117">**\<value>**</span></span>               | <span data-ttu-id="20d8e-118">Define o valor de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="20d8e-118">Defines a setting's value.</span></span> <span data-ttu-id="20d8e-119">Filho de \*\* \<configuração>\*\*.</span><span class="sxs-lookup"><span data-stu-id="20d8e-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="20d8e-120">\<aplicativoConfigurações> elemento</span><span class="sxs-lookup"><span data-stu-id="20d8e-120">\<applicationSettings> element</span></span>

<span data-ttu-id="20d8e-121">Este elemento contém todas as \*\* \<configurações>\*\* tags específicas para uma instância do aplicativo em um computador cliente.</span><span class="sxs-lookup"><span data-stu-id="20d8e-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="20d8e-122">Não define nenhum atributo.</span><span class="sxs-lookup"><span data-stu-id="20d8e-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="20d8e-123">\<usuárioConfigurações> elemento</span><span class="sxs-lookup"><span data-stu-id="20d8e-123">\<userSettings> element</span></span>

<span data-ttu-id="20d8e-124">Este elemento contém todas as \*\* \<configurações>\*\* tags específicas para o usuário que está usando o aplicativo no momento.</span><span class="sxs-lookup"><span data-stu-id="20d8e-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="20d8e-125">Não define nenhum atributo.</span><span class="sxs-lookup"><span data-stu-id="20d8e-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="20d8e-126">\<configuração> elemento</span><span class="sxs-lookup"><span data-stu-id="20d8e-126">\<setting> element</span></span>

<span data-ttu-id="20d8e-127">Este elemento define uma configuração.</span><span class="sxs-lookup"><span data-stu-id="20d8e-127">This element defines a setting.</span></span> <span data-ttu-id="20d8e-128">Tem os seguintes atributos.</span><span class="sxs-lookup"><span data-stu-id="20d8e-128">It has the following attributes.</span></span>

| <span data-ttu-id="20d8e-129">Atributo</span><span class="sxs-lookup"><span data-stu-id="20d8e-129">Attribute</span></span>        | <span data-ttu-id="20d8e-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="20d8e-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="20d8e-131">**name**</span><span class="sxs-lookup"><span data-stu-id="20d8e-131">**name**</span></span>         | <span data-ttu-id="20d8e-132">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="20d8e-132">Required.</span></span> <span data-ttu-id="20d8e-133">A identificação única da configuração.</span><span class="sxs-lookup"><span data-stu-id="20d8e-133">The unique ID of the setting.</span></span> <span data-ttu-id="20d8e-134">As configurações criadas através do `ProjectName.Properties.Settings`Visual Studio são salvas com o nome .</span><span class="sxs-lookup"><span data-stu-id="20d8e-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="20d8e-135">**Serializeas**</span><span class="sxs-lookup"><span data-stu-id="20d8e-135">**serializeAs**</span></span> | <span data-ttu-id="20d8e-136">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="20d8e-136">Required.</span></span> <span data-ttu-id="20d8e-137">O formato a ser usado para serializar o valor para texto.</span><span class="sxs-lookup"><span data-stu-id="20d8e-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="20d8e-138">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="20d8e-138">Valid values are:</span></span><br><br><span data-ttu-id="20d8e-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="20d8e-139">- `string`.</span></span> <span data-ttu-id="20d8e-140">O valor é serializado como <xref:System.ComponentModel.TypeConverter>uma seqüência usando um .</span><span class="sxs-lookup"><span data-stu-id="20d8e-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="20d8e-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="20d8e-141">- `xml`.</span></span> <span data-ttu-id="20d8e-142">O valor é serializado usando serialização XML.</span><span class="sxs-lookup"><span data-stu-id="20d8e-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="20d8e-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="20d8e-143">- `binary`.</span></span> <span data-ttu-id="20d8e-144">O valor é serializado como binário codificado por texto usando serialização binária.</span><span class="sxs-lookup"><span data-stu-id="20d8e-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="20d8e-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="20d8e-145">- `custom`.</span></span> <span data-ttu-id="20d8e-146">O provedor de configurações tem conhecimento inerente a essa configuração e serializa e desserializa-o.</span><span class="sxs-lookup"><span data-stu-id="20d8e-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="20d8e-147">\<elemento> de valor</span><span class="sxs-lookup"><span data-stu-id="20d8e-147">\<value> element</span></span>

<span data-ttu-id="20d8e-148">Este elemento contém o valor de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="20d8e-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="20d8e-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="20d8e-149">Example</span></span>

<span data-ttu-id="20d8e-150">O exemplo a seguir mostra um arquivo de configurações de aplicativo que define duas configurações com escopo de aplicativo e duas configurações com escopo do usuário:</span><span class="sxs-lookup"><span data-stu-id="20d8e-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="20d8e-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="20d8e-151">See also</span></span>

- [<span data-ttu-id="20d8e-152">Visão geral das configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="20d8e-152">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="20d8e-153">Arquitetura das configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="20d8e-153">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
