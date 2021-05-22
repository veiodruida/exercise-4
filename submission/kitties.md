# pallet-kitties
- Calls
  - `fn create_kitty`
		- `owner: AccountId`
		- `dna: u128`
		- `gender: {Male, Female}`
	- `fn breed_kitty`
		- `kitty_id_1: KittyId`
		- `kitty_id_2: KittyId`
		- `owner: AccountId`
		- `new_dna: u128`
		- `new_gender: {male, female}`
		- `kitty:Kitty`
	- `fn transfer_kitty`
		- `from: AccountId`
		- `to:AccountId`
		- `Kitty_id: KittyId`
		- Shold be Verify the Kit owner before do the transfer
	
- `Types`
  - `struct Kitty`
	- `owner: AccountId`
	- `dna: u128`
	- `gender: {male, female}`
	
- Storages
	- `Kitties: double_map AccountId, u32 => Option<Kitty>`
	- `NextKittyId: u32`
	
- Errors
	- `KittiesIdOverflow`
	- `InvalidKittyId`
	- `SameGender`

- Events
	- `KittyCreated`
		- `kitty_id:KittyId`
		- `creator: AccountId`
		- `kitty:Kitty`
	- `KittyBreaded`
		- `kitty_id:KittyId`
		- `creator: AccountId`
		- `new_dna: u128`
		- `new_gender: {male, female}`
		- `kitty:Kitty`
	- `KittyTransfered`
		- `from: AccountId`
		- `to:AccountId`
		- `kitty:Kitty`
		
- Modules
	- `fn combine_dna(dna1, dna2, selector)`
		- Return the selector (random number based in the sender DNA) & dna1 (parent) OR
		- Return the selector (random number based in the sender DNA) & dna2 (parent)
	- `fn random_value(sender)`