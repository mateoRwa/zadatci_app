# zadatci_app

Zašto Always Free instanca?
Oracle Cloud Infrastructure (OCI) u sklopu svog Always Free paketa omogućava besplatno korištenje resursa koji premašuju standardne probne pakete drugih računalnih oblaka. Konkretno, omogućava korištenje Ampere A1 Flex procesora (ARM arhitektura) do 4 OCPU-a i 24 GB RAM-a potpuno besplatno, što korisnicima pruža snažan, stabilan i besplatan poslužitelj za razvoj i produkciju manjih aplikacija.

Zašto se za Supabase ne smije odabrati Micro shape?
Ograničenje memorije (RAM): Supabase zahtijeva minimalno 4 GB RAM-a za stabilno pokretanje svih svojih servisa i kontejnera.  
Nedostatak resursa na Micro shape-u: Shape poput VM.Standard.E2.1.Micro nudi svega 1 GB RAM-a, što je premalo za pokretanje Supabase-a te će uzrokovati rušenje servisa zbog nedostatka memorije (Out Of Memory / OOM).  
Optimalan izbor: Iz tog razloga se bira VM.Standard.A1.Flex sa 2 OCPU-a i 12 GB RAM-a, čime se u potpunosti zadovoljavaju hardverski zahtjevi unutar besplatnih limita. 