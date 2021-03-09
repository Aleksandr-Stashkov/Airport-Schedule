#include <iostream>
#include <iomanip>
#include <stdlib.h>
#include <stdio.h>
#include <math.h>
#include <time.h>

using namespace std;

/*Enum*/

enum stage{
    sleep = 0,
    search1 = 1,
    wait1 = 2,
    wait2 = 3,
    search2 = 4,
    done = 5
};

inline stage& operator++(stage& current, int){
    const int i = static_cast<int>(current);
    current = static_cast<stage>((i + 1) % 6);
    return current;
}

/*Airports*/

const string AirportNames[] = {"Maimi","Moskau","Brno","Hamburg","New York","Wien","Paris","Budapest","Prague","Istambul","Toronto","Madrid","Amsterdam","Doha","London","Munich","Dusseldorf","Stuttgart","Dublin","Frankfurt","Warsaw","Geneva","Milan","Rome","Zurich","Athens"};
const int AirportTimes[] = {596, 139, 62, 46, 481, 70, 101, 84, 48, 148, 488, 157, 75, 338, 106, 68, 66, 69, 118, 61, 69, 101, 98, 108, 83, 153};
const short N_airports = sizeof(AirportNames)/sizeof(AirportNames[0]);
struct airport{
    const string * name;
    const int * t_flight;
  
    airport() : name(0), t_flight(0) {};
};
airport airports[N_airports];

/*Gate*/

struct gate{
    private:
        short timer;
    public:
        bool occ;
        short id;
    
        gate(int n) : occ(false), id(n), timer(0) {};
        void step();
        void set_timer(int t);
};
void gate::step(){
    if (timer > 0){
        timer--;
    }    
    if (timer == 0){
        occ = false;
    }
}
void gate::set_timer(int t){
    occ = true;
    timer = t;
}

/*Runway*/

struct runway{
    private:
        short timer;
    public:
        bool occ;
        short id;
    
        runway(int n) : occ(false), id(n), timer(0) {};
        void step();
        void set_timer(int t);
};
void runway::step(){
    if (timer > 0){
        timer--;
    }
    if (timer == 0){
        occ = false;
        
    }
}
void runway::set_timer(int t){
    occ = true;
    timer = t;
}

/*Plane*/

struct plane{
    private:
        short timer;
    public:
        stage st;
        string id;
        airport * ap;
        signed t_arr, t_dep, t_act;
        int delay, t_ch1, t_ch2, t_fact;
        bool dep, emerg;
        short gate_id, run_id;
        
        plane(bool dep_in, int t);
        void gen_id(plane *mass[], int N);
        void set_act(int t);
        void set_timer(int t);
        bool timer0();
        void step(signed t);
        bool get_gate(gate *mass[], int N, int t);
        bool get_run(runway *mass[], int N, int t);
};
plane::plane(bool dep_in, int t){
    short rnd = rand() %N_airports;
    
    timer = 0;
    emerg = false;
    st = sleep;
    ap = &airports[rnd];
    id = "-";
    delay = 0;
    t_act = 0;
    t_ch1 = 0;
    t_ch2 = 0;
    t_fact = 0;
    
    if (dep_in){
        dep = true;
        t_dep = rand() %t;
        t_arr = t_dep + *airports[rnd].t_flight;
    }
    else{
        dep = false;
        t_arr = rand() %t;
        t_dep = t_arr - *airports[rnd].t_flight;
    }
}
void plane::gen_id(plane *mass[], int N){
    bool x(true);
    string tmp_id("-");
    
    while (x == true){
        tmp_id = to_string(rand() %9) + to_string(rand() %9) + to_string(rand() %9);
        x = false;
        
        for (int i=0; i<N; i++){
            if (tmp_id == mass[i]->id){
                x = true;
            }
        }
    }
    
    id = tmp_id;
}
void plane::set_act(int t){
    if (dep == false){
        t_act = t_arr-t;
    }else{
        t_act = t_dep-t;
    }
}
void plane::set_timer(int t){
    timer = t;
}
bool plane::timer0(){
    if (timer == 0){
        return true;
    }else{
        return false;
    }
}
void plane::step(signed t){
    if (timer > 0){
        timer--;
    }
    if (st == search1){
        t_ch1++;
    }
    if (st == search2){
        t_ch2++;
    }
    if (timer == 0){
        if (st == wait1 || st == wait2){
            st++;
        }
    }
    if (st == sleep){
        if (t == t_act){
            st++;
        }
    }
}
bool plane::get_gate(gate *mass[], int N, int t){
    int i(0);
    
    while (i < N){
        if (mass[i]->occ == false){
            mass[i]->set_timer(t);
            set_timer(t);
            gate_id = mass[i]->id;
            st++;
            emerg = false;
            return true;
        }
        i++;
    }
    emerg = true;
    return false;
}
bool plane::get_run(runway *mass[], int N, int t){
    int i(0);
    
    while (i < N){
        if (mass[i]->occ == false){
            mass[i]->set_timer(t);
            set_timer(t);
            run_id = mass[i]->id;
            st++;
            emerg = false;
            return true;
        }
        i++;
    }
    emerg = true;
    return false;
}

/*Sorting*/

void swap(plane *pl1, plane *pl2){
    plane temp(*pl1);
    *pl1 = *pl2;
    *pl2 = temp;
}

int part_arr(plane *mass[], int low, int high){
    signed pivot = mass[high]->t_arr;
    int i(low);
    
    for (int j=low; j<high; j++){
        if (mass[j]->t_arr <= pivot){
            swap(mass[i],mass[j]);
            i++;
        }
    }
    swap(mass[i],mass[high]);
    
    return (i);
}
void quick_arr(plane *mass[], int low, int high){
    if (low < high){
        int p = part_arr(mass,low,high);
        quick_arr(mass,low,p-1);
        quick_arr(mass,p+1,high);
    }
}

int part_dep(plane *mass[], int low, int high){
    signed pivot = mass[high]->t_dep;
    int i(low);
    
    for (int j=low; j<high; j++){
        if (mass[j]->t_dep <= pivot){
            swap(mass[i],mass[j]);
            i++;
        }
    }
    swap(mass[i],mass[high]);
    
    return (i);
}
void quick_dep(plane *mass[], int low, int high){
    if (low < high){
        int p = part_dep(mass,low,high);
        quick_dep(mass,low,p-1);
        quick_dep(mass,p+1,high);
    }
}

/*Main*/

int main()
{
    /* Given */
    
    double th(1);       //time period for simulation in hours
    
    short f_arr(20);     //number of arrivals per hour
    short f_dep(20);     //number of departures per hour
    
    short N_run(3);     //number of runways
    short N_gate(40);   //number of gates
    int t_r_arr(15);    //time for a runway to clear for arriving plane in minutes
    int t_r_dep(2);     //time for a runway to clear for departing plane in minutes
    int t_r_r(5);       //time for repeat of runway request
    int t_g_arr(25);    //time for a gate to clear for arriving plane in minutes
    int t_g_dep(50);    //time for a gate to clear for departing plane in minutes
    int t_rg(2);        //time for runway-gate travel in minutes
    int t_gr(4);        //time for gate-runway travel in minutes
    
    /* Check */
    
    if (sizeof(AirportTimes)/sizeof(AirportTimes[0]) != N_airports){
        cout << "Airports' data is corrupted." << endl;
        return 0;
    }
    if (f_arr+f_dep <= 0){
        cout << "The airport is closed. No flights are available." << endl;
        return 0;
    }
    if (N_run <= 0){
        cout << "The airport is closed. All runways are under reconstruction." << endl;
        return 0;
    }
    if (N_gate <= 0){
        cout << "The airport is closed. All gates are under reconstruction." << endl;
        return 0;
    }
    if (t_rg < 0 || t_gr < 0 || t_r_r < 0 || t_g_dep < 0 || t_g_arr < 0 || t_r_dep < 0 || t_r_arr < 0){
        cout << "Some of the times set are negative or zero leading to god knows what results." << endl;
        return 0;
    }
    
    /* Initialisation */
    
    srand(time(NULL));
    
    for (int i=0; i<N_airports; i++){
        airports[i].name = &AirportNames[i];
        airports[i].t_flight = &AirportTimes[i];
    }
    
    int tmin = floor(th*60);
    int N_p_arr = round(f_arr*th);
    int N_p_dep = round(f_dep*th);
    signed t(0);
    signed t_shift(0);
    int N_done(0);
    
    plane * planes[N_p_arr+N_p_dep];
    for (int i=0; i<N_p_arr; i++){
        plane *pl = new plane(false,tmin);
        planes[i] = pl;
        planes[i]->set_act(t_r_arr+t_rg);
    }
    for (int i=0; i<N_p_dep; i++){
        plane *pl = new plane(true,tmin);
        planes[i+N_p_arr] = pl;
        planes[i+N_p_arr]->set_act(t_g_dep+t_gr+t_r_dep);
    }
    for (int i=0; i<N_p_arr+N_p_dep; i++){
        planes[i]->gen_id(planes, N_p_arr+N_p_dep);
        if (t_shift > planes[i]->t_act){
            t_shift = planes[i]->t_act;
        }
    }
    
    runway * runways[N_run];
    for (int i=0; i<N_run; i++){
        runway *rw = new runway(i+1);
        runways[i] = rw;
    }
    
    gate * gates[N_gate];
    for (int i=0; i<N_gate; i++){
        gate *gt = new gate(i+1);
        gates[i] = gt;
    }
    
    /* Processing */
    
    while (N_done != N_p_arr+N_p_dep){
        for (int i=0; i<N_gate; i++){
            if (gates[i]->occ == true){
                gates[i]->step();
            }
        }
        for (int i=0; i<N_run; i++){
            if (runways[i]->occ == true){
                runways[i]->step();
            }
        }
        for (int i=0; i<N_p_arr+N_p_dep; i++){
            if (planes[i]->st != done){
                planes[i]->step(t+t_shift);
            }
        }
        for (int i=0; i<N_p_arr+N_p_dep; i++){
            if (planes[i]->st != done && planes[i]->emerg == true){
                if (planes[i]->st == search1 && planes[i]->timer0() == true){
                    if (planes[i]->dep == false){
                        if (planes[i]->get_run(runways,N_run,t_r_arr) == false){
                            planes[i]->set_timer(t_r_r);
                        }
                    }else{
                        if (planes[i]->get_gate(gates,N_gate,t_g_dep) == false){
                            planes[i]->set_timer(1);
                        }
                    }
                }
                
                if (planes[i]->st == wait2 && planes[i]->timer0() == true){
                    if (planes[i]->dep == false){
                        planes[i]->set_timer(t_rg);
                    }else{
                        planes[i]->set_timer(t_gr);
                    }
                }
                
                if (planes[i]->st == search2 && planes[i]->timer0() == true){
                    if (planes[i]->dep == false){
                        if (planes[i]->get_gate(gates,N_gate,t_g_arr) == false){
                            planes[i]->set_timer(1);
                        }else{
                            N_done++;
                            planes[i]->t_fact = t+t_shift;
                            if (planes[i]->t_fact > planes[i]->t_arr){
                                planes[i]->delay = planes[i]->t_fact-planes[i]->t_arr;
                            }
                        }
                    }else{
                        if (planes[i]->get_run(runways,N_run,t_r_dep) == false){
                            planes[i]->set_timer(1);
                        }else{
                            N_done++;
                            planes[i]->t_fact = t+t_shift;
                            if (planes[i]->t_fact > planes[i]->t_dep){
                                planes[i]->delay = planes[i]->t_fact-planes[i]->t_dep;
                            }
                            if (planes[i]->t_ch2 > 0){
                                planes[i]->t_ch2--;
                            }
                        }
                    }
                }
            }
        }
        for (int i=0; i<N_p_arr+N_p_dep; i++){
            if (planes[i]->st != done && planes[i]->emerg == false){
                if (planes[i]->st == search1 && planes[i]->timer0() == true){
                    if (planes[i]->dep == false){
                        if (planes[i]->get_run(runways,N_run,t_r_arr) == false){
                            planes[i]->set_timer(t_r_r);
                        }
                    }else{
                        if (planes[i]->get_gate(gates,N_gate,t_g_dep) == false){
                            planes[i]->set_timer(1);
                        }
                    }
                }
                
                if (planes[i]->st == wait2 && planes[i]->timer0() == true){
                    if (planes[i]->dep == false){
                        planes[i]->set_timer(t_rg);
                    }else{
                        planes[i]->set_timer(t_gr);
                    }
                }
                
                if (planes[i]->st == search2 && planes[i]->timer0() == true){
                    if (planes[i]->dep == false){
                        if (planes[i]->get_gate(gates,N_gate,t_g_arr) == false){
                            planes[i]->set_timer(1);
                        }else{
                            N_done++;
                            planes[i]->t_fact = t+t_shift;
                            if (planes[i]->t_fact > planes[i]->t_arr){
                                planes[i]->delay = planes[i]->t_fact-planes[i]->t_arr;
                            }
                        }
                    }else{
                        if (planes[i]->get_run(runways,N_run,t_r_dep) == false){
                            planes[i]->set_timer(1);
                        }else{
                            N_done++;
                            planes[i]->t_fact = t+t_shift;
                            if (planes[i]->t_fact > planes[i]->t_dep){
                                planes[i]->delay = planes[i]->t_fact-planes[i]->t_dep;
                            }
                            if (planes[i]->t_ch2 > 0){
                                planes[i]->t_ch2--;
                            }
                        }
                    }
                }
            }
        }
        t++;
    }
    
    /* Output */
    
    quick_arr(planes,0,N_p_arr-1);
    quick_dep(planes,N_p_arr,N_p_arr+N_p_dep-1);
    
    int curt = 12*60;

    cout<<setw(40)<<"Arrivals"<<endl;
    cout
    <<setw(7)<<"\f1\u8470?\f0  |"
    <<setw(12)<<"From  |"
    <<setw(12)<<"To  |"
    <<setw(11)<<"Dep Time |"
    <<setw(11)<<"Arr Time |"
    <<setw(14)<<"Fact Arr |"
    <<setw(9)<<"Runway |"
    <<setw(7)<<"Gate |"
    <<setw(12)<<"Run Delay |"
    <<setw(13)<<"Gate Delay |"
    <<setw(6)<<"Delay"
    <<endl;
    for (int i=0; i<N_p_arr; i++){
        cout
        <<setw(4)<<planes[i]->id<<"|"
        <<setw(11)<<*(planes[i]->ap->name)<<"|"
        <<setw(12)<<"Berlin|"
        <<setw(6)<<floor((planes[i]->t_dep+curt)/60)<<":";
        if ((planes[i]->t_dep+curt)%60 > 9){
            cout<<(planes[i]->t_dep+curt)%60<<" |";
        }else{
            cout<<"0"<<(planes[i]->t_dep+curt)%60<<" |";
        }
        cout<<setw(6)<<floor((planes[i]->t_arr+curt)/60)<<":";
        if ((planes[i]->t_arr+curt)%60 > 9){
            cout<<(planes[i]->t_arr+curt)%60<<" |";
        }else{
            cout<<"0"<<(planes[i]->t_arr+curt)%60<<" |";
        }
        cout<<setw(9)<<floor((planes[i]->t_fact+curt)/60)<<":";
        if ((planes[i]->t_fact+curt)%60 > 9){
            cout<<(planes[i]->t_fact+curt)%60<<" |";
        }else{
            cout<<"0"<<(planes[i]->t_fact+curt)%60<<" |";
        }
        cout<<setw(5)<<planes[i]->run_id<<"   |"
        <<setw(4)<<planes[i]->gate_id<<"  |";
        if (planes[i]->t_ch1 == 0){
            cout<<setw(12)<<"- |";
        }else{
            cout<<setw(7)<<floor(planes[i]->t_ch1/60)<<":";
            if (planes[i]->t_ch1%60 > 9){
                cout<<planes[i]->t_ch1%60<<" |";
            }else{
                cout<<"0"<<planes[i]->t_ch1%60<<" |";
            }
        }
        if (planes[i]->t_ch2 == 0){
            cout<<setw(13)<<"- |";
        }else{
            cout<<setw(8)<<floor(planes[i]->t_ch2/60)<<":";
            if (planes[i]->t_ch2%60 > 9){
                cout<<planes[i]->t_ch2%60<<" |";
            }else{
                cout<<"0"<<planes[i]->t_ch2%60<<" |";
            }
        }
        if (planes[i]->delay == 0){
            cout<<setw(6)<<"-"<<endl;
        }else{
            cout<<setw(3)<<floor(planes[i]->delay/60)<<":";
            if (planes[i]->delay%60 > 9){
                cout<<planes[i]->delay%60<<endl;
            }else{
                cout<<"0"<<planes[i]->delay%60<<endl;
            }
        }
    }
    
    cout<<setw(40)<<"Departures"<<endl;
    cout
    <<setw(7)<<"\f1\u8470?\f0  |"
    <<setw(12)<<"From  |"
    <<setw(12)<<"To  |"
    <<setw(11)<<"Dep Time |"
    <<setw(11)<<"Arr Time |"
    <<setw(14)<<"Fact Dep |"
    <<setw(9)<<"Runway |"
    <<setw(7)<<"Gate |"
    <<setw(12)<<"Run Delay |"
    <<setw(13)<<"Gate Delay |"
    <<setw(6)<<"Delay"
    <<endl;
    for (int i=N_p_arr; i<N_p_arr+N_p_dep; i++){
        cout
        <<setw(4)<<planes[i]->id<<"|"
        <<setw(12)<<"Berlin|"
        <<setw(11)<<*(planes[i]->ap->name)<<"|"
        <<setw(6)<<floor((planes[i]->t_dep+curt)/60)<<":";
        if ((planes[i]->t_dep+curt)%60 > 9){
            cout<<(planes[i]->t_dep+curt)%60<<" |";
        }else{
            cout<<"0"<<(planes[i]->t_dep+curt)%60<<" |";
        }
        cout<<setw(6)<<floor((planes[i]->t_arr+curt)/60)<<":";
        if ((planes[i]->t_arr+curt)%60 > 9){
            cout<<(planes[i]->t_arr+curt)%60<<" |";
        }else{
            cout<<"0"<<(planes[i]->t_arr+curt)%60<<" |";
        }
        cout<<setw(9)<<floor((planes[i]->t_fact+curt)/60)<<":";
        if ((planes[i]->t_fact+curt)%60 > 9){
            cout<<(planes[i]->t_fact+curt)%60<<" |";
        }else{
            cout<<"0"<<(planes[i]->t_fact+curt)%60<<" |";
        }
        cout<<setw(5)<<planes[i]->run_id<<"   |"
        <<setw(4)<<planes[i]->gate_id<<"  |";
        if (planes[i]->t_ch2 == 0){
            cout<<setw(12)<<"- |";
        }else{
            cout<<setw(7)<<floor(planes[i]->t_ch2/60)<<":";
            if (planes[i]->t_ch2%60 > 9){
                cout<<planes[i]->t_ch2%60<<" |";
            }else{
                cout<<"0"<<planes[i]->t_ch2%60<<" |";
            }
        }
        if (planes[i]->t_ch1 == 0){
            cout<<setw(13)<<"- |";
        }else{
            cout<<setw(8)<<floor(planes[i]->t_ch1/60)<<":";
            if (planes[i]->t_ch1%60 > 9){
                cout<<planes[i]->t_ch1%60<<" |";
            }else{
                cout<<"0"<<planes[i]->t_ch1%60<<" |";
            }
        }
        if (planes[i]->delay == 0){
            cout<<setw(6)<<"-"<<endl;
        }else{
            cout<<setw(3)<<floor(planes[i]->delay/60)<<":";
            if (planes[i]->delay%60 > 9){
                cout<<planes[i]->delay%60<<endl;
            }else{
                cout<<"0"<<planes[i]->delay%60<<endl;
            }
        }
    }
    
    return 0;
}