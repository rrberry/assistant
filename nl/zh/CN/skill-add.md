---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-08"

subcollection: assistant

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:deprecated: .deprecated}
{:important: .important}
{:note: .note}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# 创建技能
{: #skill-add}

{{site.data.keyword.conversationshort}} 服务的自然语言处理是在*对话技能*中定义的；对话技能是包含定义会话流的所有工件的容器。
{: shortdesc}

您可以向一个助手添加一个技能。

可以从头开始创建技能，使用 IBM 提供的样本技能，或从 JSON 文件导入技能。要添加技能，请完成以下步骤：

1.  如果尚未创建 {{site.data.keyword.conversationshort}} 服务实例，请首先执行这个一次性过程。否则，请跳过此步骤。

    1.  转至 {{site.data.keyword.cloud_notm}}“目录”中的 [{{site.data.keyword.conversationshort}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/catalog/services/watson-assistant) 页面。

    1.  注册 {{site.data.keyword.cloud_notm}} 帐户或登录。

        如果未选择其他资源组，服务实例将在**缺省**资源组中创建，并且日后*不能*更改。*缺省*资源组通常足以满足需求。但是，如果要了解有关资源组的更多信息，请参阅 [{{site.data.keyword.Bluemix_notm}} 文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/docs/resources?topic=resources-bp_resourcegroups#bp_resourcegroups){: new_window}。

        可以使用一个服务实例来开发、测试和部署助手，因此不要为不同类型的部署环境创建不同的资源组。
        {:tip}

        使用高端套餐时，可以创建多个实例。实例必须全部在同一资源组中创建。

    1.  单击**创建**。

    1.  单击**启动工具**。如果系统提示您登录到该工具，请提供您的 {{site.data.keyword.cloud_notm}} 凭证。

1.  单击**技能**选项卡。

    对于使用 {{site.data.keyword.conversationshort}} 服务（先前称为 Watson Conversation）的一般可用版本构建的任何工作空间，如果已创建或已被授予其开发者角色访问权，那么将看到这些工作空间在此处作为对话技能列出。
    {: note}

1.  单击**新建**。

1.  执行下列其中一个操作：

    - 要从头开始创建技能，请单击**创建技能**。
    - 要添加随服务一起提供的样本技能以作为您自己的技能的起点，或作为示例以在自行创建技能之前进行探索，请单击**使用样本技能**，然后单击要使用的样本。

      样本技能已添加到技能列表中。该技能未与任何助手相关联。请跳过本过程中的其余步骤。

    - 要将现有技能添加到此服务实例，可以将其作为 JSON 文件导入。单击**导入技能**，然后单击**选择 JSON 文件**，并选择要导入的 JSON 文件。

      **重要信息：**

      - 导入的 JSON 文件必须使用 UTF-8 编码，而不使用字节顺序标记 (BOM) 编码。
      - 技能 JSON 文件的最大大小为 10 MB。如果需要导入更大的技能，请考虑在导入技能后单独导入意向和实体。（您还可以使用 REST API 导入更大的技能。有关更多信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/apidocs/assistant?curl=#create-workspace){: new_window}。）
      - JSON 不能包含制表符、换行符或回车符。

      指定要包含的数据：

        - 如果要导入已导出技能的完整副本（包括对话），请选择**所有内容（意向、实体和对话）**。
        - 如果要使用已导出技能中的意向和实体，但计划构建新的对话，请选择**意向和实体**。

      单击**导入**。

      如果导入技能时遇到问题，请参阅[有关技能导入问题的故障诊断](#skill-add-import-errors)。

1.  指定技能的详细信息：

    - **名称**：名称，长度不超过 100 个字符。名称是必填的。
    - **描述**：可选的描述，长度不超过 200 个字符。
    - **语言**：将对技能进行训练以理解用户输入的语言。缺省值为“英语”。

创建技能后，该技能即会在“技能”页面上显示为磁贴。现在，您可以开始识别希望对话技能处理的用户目标。

- 要向技能添加预构建的意向，请参阅[使用内容目录](/docs/services/assistant?topic=assistant-catalog)。
- 要定义您自己的意向，请参阅[定义意向](/docs/services/assistant?topic=assistant-intents)。

在将对话技能添加到助手并部署助手之前，对话技能无法与客户交互。请参阅[创建助手](/docs/services/assistant?topic=assistant-assistant-add)。

## 有关技能导入问题的故障诊断
{: #skill-add-import-errors}

如果您收到一条消息，指示技能包含的工件数超过服务套餐所施加的限制，请完成以下步骤以成功导入技能：

1.  购买具有更高工件限制的套餐。
1.  在新套餐中创建服务实例。
1.  将技能导入到新服务实例。
1.  对技能进行编辑，以使其符合要继续使用的套餐的工件限制需求。例如，您可能需要减少对话树中使用的对话节点数。
1.  通过下载已编辑的技能来导出该技能。
1.  重试将已编辑的技能导入到所需套餐中的原始服务实例。

## 向助手添加技能
{: #skill-add-to-assistant}

您可以向一个助手添加一个技能。必须打开助手磁贴，并在助手配置页面中向该助手添加技能；无法在技能配置页面中选择将使用该技能的助手。一个对话技能可以由多个助手使用。

1.  在“助手”选项卡中，单击以打开要向其添加技能的助手的磁贴。

1.  单击**添加对话技能**。

1.  单击**添加现有技能**。

    在显示的可用技能中，单击要添加的技能。

    从此处添加技能时，可获取开发版本。如果要添加特定技能版本，请改为在技能的*版本历史记录*选项卡中进行添加。

## 技能限制
{: #skill-add-limits}

可以在单个服务实例中创建的技能数取决于 {{site.data.keyword.conversationshort}} 套餐。服务实例中可用的任何样本对话技能都不会计入限制，除非您编辑或复制这些技能。

|服务套餐          |每个服务实例的技能数|
|------------------|----------------------------:|
|高级                                 |50|
|增强版            |50|
|标准                                 |20                            |
|Lite*            |5 |
{: caption="服务套餐详细信息" caption-side="top"}

* 轻量套餐服务实例中未使用的技能处于不活动状态的时间达到 30 天后，可能会将其删除以释放空间。

## 下载对话技能
{: #skill-add-download}

可以下载 JSON 格式的对话技能。例如，如果要在 {{site.data.keyword.conversationshort}} 服务的不同实例中使用同一对话技能，您可能希望下载该技能。可以从一个实例下载技能，然后将其作为新的对话技能导入到其他实例。

要下载对话技能，请完成以下步骤：

1.  在“技能”页面上或在使用技能的助手的配置页面上，找到对话技能磁贴。

1.  单击 ![打开和关闭选项列表](images/kabob-beta.png) 图标，然后选择**下载 JSON**。

1.  指定 JSON 文件的名称以及保存该文件的位置，然后单击**保存**。

还可以使用 API 来导出技能。请在请求中包含 `export=true` 参数。有关更多详细信息，请参阅 [API 参考](https://cloud.ibm.com/apidocs/assistant#get-information-about-a-workspace)。

## 删除技能
{: #skill-add-delete}

可以删除可访问的任何技能，但助手正在使用的技能除外。如果技能正在使用中，那么必须从正在使用该技能的助手中将其除去，然后才能对其执行删除操作。

确保在删除技能之前，核实是否有其他任何人可能正在使用该技能。
{: tip}

要删除技能，请完成以下步骤：

1.  了解是否有任何助手正在使用该技能。在“技能”选项卡中，找到要删除的技能的磁贴。**助手**字段会列出当前使用技能的助手。

1.  如果要删除的技能与助手相关联，请通过完成以下步骤将其从助手中除去：

    - 从正在使用技能的助手中除去该技能之前，请与该助手的所有者核实。
    - 打开“助手”选项卡，然后单击以打开助手磁贴。
    - 找到要删除的技能的磁贴。单击 ![打开和关闭选项列表](images/kabob-beta.png) 图标，然后选择**除去**。
    - 对使用该技能的其他任何助手重复上述步骤。
    - 返回到“技能”选项卡，然后找到要删除的技能的磁贴。

1.  单击 ![打开和关闭选项列表](images/kabob-beta.png) 图标，然后选择**删除**。确认此删除操作。

## 与团队成员共享对话技能
{: #skill-add-invite-others}

创建服务实例后，您可以授予其他人对该实例的访问权。您可以与其他人一起定义训练数据并构建对话。

**重要信息**：一次只能有一个人编辑意向、实体或对话节点。如果多个人同时对同一个项进行处理，那么仅会应用最后保存其更改的人员所做的更改。不会保留其他人在同一时间范围内所执行并先保存的更改。请与团队成员协调您计划进行的更新，以避免任何人所做的工作丢失。

要与其他人共享对话技能，您必须授予他们对托管该技能的服务实例的访问权。请注意，您邀请的人员将能够访问此服务实例托管的任何技能。

1.  记下当前实例名称，该名称显示在当前页面的顶部。
1.  单击页面标题中的“用户”![用户](images/user-icon2.png) 图标，然后从下拉列表中选择**管理用户**。

1.  单击**邀请用户**，然后输入团队中您希望向其授予访问权的人员的电子邮件地址。

    如果授予某人对已由 Cloud Foundry 管理的服务实例的访问权，那么此人可能已作为受邀用户列出。单击此人的名称以打开用户的访问管理设置。单击**分配访问权**，然后选择**分配对资源的访问权**。

1.  在*服务*部分中，至少进行以下选择：

    - **服务**：{{site.data.keyword.conversationshort}}
    - **分配平台访问角色**：操作员

    有关平台管理角色的更多信息，请参阅 [IAM 访问权 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/iam?topic=iam-userroles)。（缺省情况下，{{site.data.keyword.conversationshort}} 不会利用服务访问角色。）

    对于由 Cloud Foundry 管理的旧实例，必须展开 *Cloud Foundry 访问权*部分，选择组织，然后为人员分配**开发者**空间角色。
    {: note}

1.  单击**邀请用户**。

    如果要编辑现有用户的访问权，请单击**分配访问权**。

您邀请的人员下次登录到 {{site.data.keyword.cloud_notm}} 时，您的帐户将包含在其帐户列表中。如果他们选择了您的帐户，那么他们可以看到您的服务实例，并打开和编辑您的技能。

随着更多人参与对话技能开发，可能会发生意外更改，包括技能删除。请考虑定期创建对话技能的备份副本，以便在必要时可以回滚到较早的版本。要创建备份，只需[将技能下载为 JSON 文件](#skill-add-download)。
