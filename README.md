{ 
TCanvas c1 = new TCanvas("c1","c1",50,50,800,600); 
c1->SetFillColor(0);
gStyle->SetOptStat(0);
gStyle->SetPalette(1);
TNtuple *nt = new TNtuple("nt","ntuple","x:y:z");
Int_t i; TRandom r; Double_t x,y,z; 

for (i=0;i<10000;i++){ 
do {
x=r.Uniform(-10,10); y=r.Uniform(-10,10); z=r.Uniform(-10,10); 
   } 
while (sqrt(xx+yy+zz)>10.0);
nt->Fill(x,y,z); 
                     } 
printf("ntuple has %i entries\n",nt->GetEntries());
c1->Divide(2,2); 
c1->cd(1);
nt->Draw("z:y:x","");
c1->cd(2); 
nt->Draw("z:y:x","x>0");
c1->cd(3);
nt->SetMarkerStyle(8);
nt->SetMarkerColor(4); 
nt->Draw("z:y","abs(x)<0.5",""); 
nt->SetMarkerColor(2);
nt->Draw("z:y","abs(x-2)<0.5","same");
nt->SetMarkerColor(3);
nt->Draw("z:y","abs(x-4)<0.5","same");
nt->SetMarkerColor(4);
nt->Draw("z:y","abs(x-6)<0.5","same");
nt->SetMarkerColor(5); 
nt->Draw("z:y","abs(x-8)<0.5","same");
c1->cd(4); nt->Draw("z:y","x>5","colz");
c1->cd();
}
