id: inventory
kind: recipe
title: Inventário e itens: pegar, empilhar, usar, equipar | Inventory and items: pick up, stack, use, equip
keys: inventario, inventário, inventory, item, itens, items, mochila, bolsa, backpack, bag, slot, slots, pilha, stack, empilhar, peso, weight, carga, equipar, equip, equipamento, equipment, arma na mao, weapon in hand, socket, pickup, pegar item, coletar, collect, loot, soltar item, drop item, pocao, potion, consumivel, consumable, item definition, definicao de item, add item, remove item, has item, get item count, use item, equip item, unequip item, drop item, get slot, move item, find item by tag, split stack, sort inventory, wbp_inventory, grade de itens, arrastar e soltar, drag and drop, salvar inventario, save inventory, bau, chest, transfer item
--- pt
Um **item** é um Data Asset do tipo **Item Definition** (Content Browser > Adicionar > **Definição de Item**): nome exibido, descrição, ícone (uma textura), malha no mundo, **Max Stack** (tamanho da pilha), **Weight** (kg), **Tags** (`Item.Weapon`, `Item.Consumable`...), **Equip Slot** (Right Hand, Head...), **Socket** (o osso; vazio: o do slot) e **Value**. Nos nós e scripts o item é o **nome do asset**: `DA_Potion`.
- No ator: **Details > Adicionar > Inventory** (ou o componente Inventory no Blueprint): slots, peso máximo, itens iniciais, pegar ao encostar e a tecla de interagir (E).
- **Ator Pickup** (Place Actors > Pickup): o item no chão, gira e é pego ao encostar ou com a tecla de interagir; com Respawn Time ele volta.
- Nós (categoria **Inventory**): **Add Item** (as pilhas enchem antes dos slots vazios; Remainder é o que não coube), **Remove Item**, **Has Item**, **Get Item Count**, **Use Item** (um item `Item.Consumable` gasta um), **Equip Item** / **Unequip Item** (a malha vai para o socket do Skeletal Mesh), **Drop Item**, **Get Slot**, **Move Item**, **Split Stack**, **Sort Inventory**, **Find Item by Tag**, **Transfer Item** (baú), **Get Item Info**.
- Eventos: **Event On Inventory Changed**, **Event On Item Used** (Item), **Event On Item Equipped** (Item, Slot Name).
- Tela pronta: Content Browser > Adicionar > **Widget de Inventário (WBP_Inventory)** (vai para Content/UI): arrastar move ou troca, arrastar para o equipamento equipa, arrastar para fora solta no mundo, botão direito usa, duplo clique equipa, dica com a descrição.
- **Save Game to Slot** salva o inventário e o equipamento do ator junto com as variáveis.

```diagram steps
Pickup no chão | o Character encosta (ou aperta E) | Add Item: pilhas, depois slots vazios | Event On Inventory Changed | WBP_Inventory mostra
```
```blueprint
Event BeginPlay -> Add Item ( Target = self, Item = "DA_Potion", Count = 3 )
Event Key I -> Create Widget ( WBP_Inventory ) -> Add to Viewport -> Set Show Mouse Cursor ( true )
Event Key H -> Branch ( Has Item ( Item = "DA_Potion" ) ) -> Use Item ( Item = "DA_Potion" )
Event On Item Used ( Item ) -> Print String ( Format Text ( "Usou {0}", Item ) )
```
```real
class Hero extends Character
    event BeginPlay()
        AddItem("DA_Potion", 3)
        AddItem("DA_Sword", 1)
        EquipItem("DA_Sword")

    event OnItemUsed(item: string)
        print("usou " + item)

    event OnInventoryChanged()
        print("poções: " + GetItemCount("DA_Potion"))
```
--- en
An **item** is a Data Asset of the type **Item Definition** (Content Browser > Add > **Item Definition**): display name, description, icon (a texture), world mesh, **Max Stack**, **Weight** (kg), **Tags** (`Item.Weapon`, `Item.Consumable`...), **Equip Slot** (Right Hand, Head...), **Socket** (the bone; empty: the slot's) and **Value**. In the nodes and scripts the item is the **asset's name**: `DA_Potion`.
- On the actor: **Details > Add > Inventory** (or the Inventory component in the Blueprint): slots, max weight, starting items, picking up on touch and the interact key (E).
- **Pickup actor** (Place Actors > Pickup): the item on the ground, it spins and is taken on touch or with the interact key; with a Respawn Time it comes back.
- Nodes (category **Inventory**): **Add Item** (the stacks fill before the empty slots; Remainder is what didn't fit), **Remove Item**, **Has Item**, **Get Item Count**, **Use Item** (an `Item.Consumable` item spends one), **Equip Item** / **Unequip Item** (the mesh goes to the Skeletal Mesh's socket), **Drop Item**, **Get Slot**, **Move Item**, **Split Stack**, **Sort Inventory**, **Find Item by Tag**, **Transfer Item** (a chest), **Get Item Info**.
- Events: **Event On Inventory Changed**, **Event On Item Used** (Item), **Event On Item Equipped** (Item, Slot Name).
- A ready screen: Content Browser > Add > **Inventory Widget (WBP_Inventory)** (it goes to Content/UI): dragging moves or swaps, dragging onto the equipment equips, dragging out drops into the world, right click uses, double click equips, a tip with the description.
- **Save Game to Slot** saves the actor's inventory and equipment with its variables.

```diagram steps
Pickup on the ground | the Character touches it (or presses E) | Add Item: stacks, then empty slots | Event On Inventory Changed | WBP_Inventory shows it
```
```blueprint
Event BeginPlay -> Add Item ( Target = self, Item = "DA_Potion", Count = 3 )
Event Key I -> Create Widget ( WBP_Inventory ) -> Add to Viewport -> Set Show Mouse Cursor ( true )
Event Key H -> Branch ( Has Item ( Item = "DA_Potion" ) ) -> Use Item ( Item = "DA_Potion" )
Event On Item Used ( Item ) -> Print String ( Format Text ( "Used {0}", Item ) )
```
```real
class Hero extends Character
    event BeginPlay()
        AddItem("DA_Potion", 3)
        AddItem("DA_Sword", 1)
        EquipItem("DA_Sword")

    event OnItemUsed(item: string)
        print("used " + item)

    event OnInventoryChanged()
        print("potions: " + GetItemCount("DA_Potion"))
```
