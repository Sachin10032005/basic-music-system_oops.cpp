#include<iostream>
#include<string>//string header fro representing music name
#include<vector>

using namespace std;

class Song{
    private:
        string title;
        string artist;
        string genre;
        double duration;//in minutes only
    public:
        //creating constructor
        Song(string title, string artist,string genre, double duration){
            this->title = title;
            this->artist = artist;
            this->genre = genre;
            this->duration = duration;
        }    
        //using the getters
        string get_Title() const {return title;}
        string get_artist() const {return artist;}
        string get_genre() const {return genre;}
        double get_duration() const{return duration;}
        //function for displaying song informtion
        void display_song_info() const {
        cout<<"Title:"<<title<<endl;
        cout<<"Artist:"<<artist<<endl;
        cout<<"Genre:"<<genre<<endl;
        cout<<"Duration:"<<duration<<endl;

        }
};

class Playlist{
    private:
    string name;
    vector<Song>songs;
    public:
    //creating constructor
    Playlist(string name){
        this->name = name;
    }

    //function for adding song to the playlist
    void addSong(const Song& song){
        songs.push_back(song);

    }
    //function for displaying playlist information
    void display_info() const {
        cout<<"Playlist:"<<name<<endl;
        cout<<"-------------------------"<<endl;
        for(const auto&song : songs){
            song.display_song_info();
            cout<<"-----------------------"<<endl;

        }

    }
};
class MusicPlayer {
private:
    vector<Playlist> playlists;

public:
    // Add playlist to music player
    void addPlaylist(const Playlist& playlist) {
        playlists.push_back(playlist);
    }

    // Display all playlists
    void displayPlaylists() const {
        cout << "All Playlists" << endl;
        cout << "--------------------------" << endl;
        for (const auto& playlist : playlists) {
            playlist.display_info();
        }
    }
};

int main (){
    //some popular songs
    Song song1("old skool","Sidhu Moosewala", "Gangster", 4.10);
    Song song2("Excuses", "A.P. Dhillon", "Emotional",2.45);
    Song song3("Do You Know","Diljeet", "Timepass",4.56);

        // Create a playlist
    Playlist playlist1("My Favorites");
    playlist1.addSong(song1);
    playlist1.addSong(song2);

    // Create another playlist
    Playlist playlist2("Classic Rock");
    playlist2.addSong(song1);
    playlist2.addSong(song3);

    // Create a music player
    MusicPlayer player;

    // Add playlists to the music player
    player.addPlaylist(playlist1);
    player.addPlaylist(playlist2);

    // Display all playlists
    player.displayPlaylists();

    return 0;
 }
