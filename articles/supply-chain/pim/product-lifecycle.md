---
# required metadata

title: Product lifecycle state
description: A product lifecycle state documents the lifecycle state of a released product or product variant.  
author: cvocph
manager: AnnBe
ms.date: 12/08/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: EcoResProductLifecycleState, EcoResReleasedProductLifecycleStateChanges
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: yuyus
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: cvocph
ms.dyn365.ops.version: 7.3 
ms.search.validFrom: 2017-12-31

---

# Product lifecycle state 

[!include[banner](../includes/banner.md)]


A product lifecycle state documents the lifecycle state of a released product or product variant. Product lifecycle states are defined 
by the user, typically a product manager or a product master data manager. Specific business processes, such as master planning, can be 
affected by a specific lifecycle state.   
 
A released product or product variant can be associated with a product lifecycle state that documents in which lifecycle state a 
specific product or variant is currently in. You can define any number of product lifecycle states by assigning a state name and 
description. You can select one lifecycle state as the default state for new released products. Released product variants inherit 
their product lifecycle state from their released product master on creation. When changing the lifecycle state on a released product master, you can choose to update all existing variants that have the same original state.  

## Create a new product lifecycle state 
 
- To create a new product lifecycle state, play or read the task guide **Create a new product lifecycle state**. 

-  To create a default product lifecycle state, play or read the task guide **Create a default product lifecycle state**.   

## Associate product lifecycle states to released products  

There are multiple ways to associate a product lifecycle state to released products or product variants.

-  On creation of a new released product, the default **Product lifecycle state** is automatically assigned. 
-  On release of a product to a legal entity, the default **Product lifecycle state** is automatically assigned. 
-  On release of a product variant to a legal entity, the **Product lifecycle state** associated to the released product master in this 
legal entity is automatically assigned to the new variant. 

You can manually update the product lifecycle state by using: 

-	 The **Released products** list page or **Details view**. 
-  The **Released product variants** list page or **Details view**. 
-  Find the obsolete products or product variants based on demand and associate a lifecycle state.  

For detailed information about how to associate product lifecycle states, play or read the following two task guides.

-  To associate a product lifecycle state to a released product master, play or read the task guide **Assign a product lifecycle state to a released product master**. 

-  To associate a product lifecycle state to a release product, play or read the task guide **Assign a product lifecycle state to a released product**. 

## Impact on master planning 

The product lifecycle state has only one control flag: **Is active for planning**. By default, this is set to **Yes** for all created 
product lifecycle states, but it can be changed to **No**. When set to **No**, the associated released products or released product variants are: 

-  Excluded from master planning. 
-  Excluded from BOM-level calculation. 

For detailed information about how to use product lifecycle state to exclude products from master planning and BOM-level calculation, play or read the task guide **Create a product lifecycle state to exclude products from Master planning**.

> [!NOTE]
> For performance reasons, it is highly recommended to associate all obsolete released products or product variants, especially when 
working with non-reusable product configuration variants, with a product lifecycle state that is deactivated for master planning.  
 
## Default migration, import, and export 

The product lifecycle states are not supported by data entities, and the lifecycle state cannot be set to a variable state through the 
released product data entities.

-  On migration from previous releases, the lifecycle state of all products and product variants will be blank.  
-  When importing released products through a data entity, the default lifecycle state will be applied on creation.  
-  When importing released product variants through a data entity, the product lifecycle state of the released product master will be imported.   
 
## Find obsolete products and products variants 
 
You can run a simulation analysis to find the obsolete released products or product variants and then update their product lifecycle status. To find obsolete products, play and read the task guide **Find obsolete product variants and assign a product lifecycle state**. This task guide shows how to find obsolete released products or product variants and how to associate a product lifecycle state to the obsolete products. It also shows hot to view the simulation results and assess how many products and product variants will be associated with a new product lifecycle state when running the update without simulation.  
 
By running the analysis in a simulation mode, the products and product variants identified as obsolete are displayed in a specific form, where they can easily be reviewed. The analysis searches for transactions and specific master data to identify products that have no demand within a variable period and no master data that can result in demand. New released products within a variable period can be excluded from the analysis. When the analysis simulation returns the expected result, the user can run the analysis and set a new product lifecycle state to all products identified as obsolete by the analysis.  
 
> [!NOTE]
> Note that all analysis and updates must be done within the same legal entity.  
 
## Criteria to select and update released products or product variants 
 
Use the following criteria to select and update the released products and product variants: 

-	 The product lifecycle state of the product or product variant must be different from the new desired state. 
-  The product or product variant was created some days ago based on the number of days that you enter in the selection dialog box. 
-  There are no open production orders (= status < ended) for the product or product variant. 
-  There are no open inventory transactions (= status issue ReservPhysical to QuotationIssue or status receipt Registrered to QuotationReceipt) for the product or product variant. 
-  There are no inventory transactions within the last number of days for the product or product variant. 
-  There is no future demand or supply forecast for the product or product variant.  
-  No minimum stock level has been set in item coverage for the product or product variant. 
-  No active fixed quantity kanban rule for the product or product variant.  
-  No service order line for the product or product variant. 
-  No active or future sales or purchase agreement lines for the product or product variant. 
-  The product or product variant is not used in a BOM that is associated with a non-expired approved BOM version for a product or variant that is active for planning.

## Related topics

-  Create a new product lifecycle state
-  Create a default new product lifecycle state
-  Assign a product lifecycle state to a released product master
-  Assign a product lifecycle state to a released product
-  Find obsolete product variants and assign a product lifecycle state
-  Create a product lifecycle state to exclude products from Master planning
